<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Learn Web Dev with M Nazim</title>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; }
        body { background-color: #f4f7f6; color: #333; padding: 20px; }
        .container { max-width: 800px; margin: 0 auto; }
        
        header { text-align: center; padding: 40px 20px; background: linear-gradient(135deg, #1e3c72, #2a5298); color: white; border-radius: 10px; margin-bottom: 30px; position: relative; }
        header h1 { font-size: 2.2rem; }
        
        /* Secret Tap Target Logo Style */
        .secret-logo { width: 60px; height: 60px; background: rgba(255,255,255,0.2); margin: 0 auto 10px auto; border-radius: 50%; display: flex; align-items: center; justify-content: center; cursor: pointer; font-size: 1.5rem; user-select: none; }

        .auth-panel { text-align: right; margin-bottom: 15px; }
        .btn-google { background: #db4437; color: white; padding: 10px 15px; border: none; border-radius: 5px; font-weight: bold; cursor: pointer; }
        
        .payment-card { background: white; padding: 30px; border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.1); text-align: center; margin-bottom: 20px; display: none; }
        .account-details { background: #eef2f7; padding: 15px; border-radius: 5px; margin: 20px 0; text-align: left; }
        .input-field { width: 100%; padding: 12px; margin-bottom: 15px; border: 1px solid #ddd; border-radius: 5px; }
        .btn-submit { width: 100%; padding: 12px; background: #2a5298; color: white; border: none; border-radius: 5px; font-weight: bold; cursor: pointer; }

        #course-content { display: none; }
        .week-card { background: white; padding: 25px; border-radius: 8px; margin-bottom: 20px; border-left: 5px solid #2a5298; }

        /* Secret Admin Modal Styles */
        .admin-modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.8); z-index: 1000; justify-content: center; align-items: center; padding: 20px; }
        .admin-content { background: white; padding: 25px; border-radius: 8px; max-width: 600px; width: 100%; max-height: 85vh; overflow-y: auto; position: relative; }
        .close-admin { position: absolute; top: 10px; right: 15px; font-size: 1.5rem; cursor: pointer; }
        .student-row { background: #f9f9f9; padding: 15px; margin-top: 15px; border-radius: 5px; border: 1px solid #eee; }
        .preview-img { max-width: 100%; max-height: 150px; margin-top: 10px; border-radius: 5px; display: block; }
        .btn-approve { background: #4caf50; color: white; padding: 6px 12px; border: none; border-radius: 4px; cursor: pointer; margin-top: 10px; font-weight: bold; }
    </style>
</head>
<body>

<div class="container">
    <div class="auth-panel">
        <span id="user-display">🔒 Please Login</span>
        <button id="btn-login" class="btn-google" style="margin-left: 10px;">Login with Google</button>
    </div>

    <header>
        <div id="secret-trigger" class="secret-logo">🎓</div>
        <h1>Web Development Course</h1>
        <p>Mentor: Zeeshan Bhai</p>
    </header>

    <main>
        <div id="payment-gate" class="payment-card">
            <h2>🔒 Premium Course Content is Locked</h2>
            <div class="account-details">
                <p><strong>📱 JazzCash:</strong> 03705519562 (Zeeshan)</p>
                <p><strong>📱 EasyPaisa:</strong> 03379827882 (Zeeshan)</p>
            </div>
            <form id="payment-form">
                <input type="text" id="tid-input" placeholder="Enter 11-digit TID Number" required class="input-field">
                <label style="font-weight: bold; display: block; margin-bottom: 5px; text-align: left;">Upload Receipt Screenshot:</label>
                <input type="file" id="screenshot-input" accept="image/*" required class="input-field">
                <button type="submit" class="btn-submit">Submit Payment Proof</button>
            </form>
        </div>

        <div id="course-content">
            <div class="week-card">
                <h3>Week 1: HTML Basics (Unlocked 🎉)</h3>
                <p style="margin-top:10px;">Welcome! Start learning HTML with Termux and Acode editor...</p>
            </div>
        </div>
    </main>
</div>

<div id="admin-panel" class="admin-modal">
    <div class="admin-content">
        <span id="close-modal" class="close-admin">&times;</span>
        <h2 style="color: #1e3c72; border-bottom: 2px solid #1e3c72; padding-bottom: 10px;">😎 Zeeshan Control Panel</h2>
        <div id="student-requests-list" style="margin-top: 15px;">
            <p style="color: #666;">No pending verification requests found.</p>
        </div>
    </div>
</div>

<script type="module">
  import { initializeApp } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-app.js";
  import { getFirestore, doc, setDoc, getDoc, collection, getDocs, updateDoc } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-firestore.js";
  import { getAuth, signInWithPopup, GoogleAuthProvider, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-auth.js";

  const firebaseConfig = {
    apiKey: "AIzaSyCsgXPW-h2NzAHMrDBIL_HjlU8wSpcgzvI",
    authDomain: "course-3cc77.firebaseapp.com",
    databaseURL: "https://course-3cc77-default-rtdb.firebaseio.com",
    projectId: "course-3cc77",
    storageBucket: "course-3cc77.firebasestorage.app",
    messagingSenderId: "136140432667",
    appId: "1:136140432667:web:9f543dc3db8683944ddfbe"
  };

  const app = initializeApp(firebaseConfig);
  const db = getFirestore(app);
  const auth = getAuth(app);
  const provider = new GoogleAuthProvider();
  let currentUser = null;

  // Login
  document.getElementById("btn-login").addEventListener("click", () => {
      signInWithPopup(auth, provider).catch(err => alert("Error: " + err.message));
  });

  // Auth Monitor
  onAuthStateChanged(auth, async (user) => {
    if (user) {
      currentUser = user;
      document.getElementById("user-display").innerText = "👤 " + user.displayName;
      document.getElementById("btn-login").style.display = "none";
      checkUserStatus();
    }
  });

  async function checkUserStatus() {
      const userDoc = await getDoc(doc(db, "users", currentUser.uid));
      if (userDoc.exists() && userDoc.data().status === "paid") {
          document.getElementById("payment-gate").style.display = "none";
          document.getElementById("course-content").style.display = "block";
      } else {
          document.getElementById("payment-gate").style.display = "block";
          document.getElementById("course-content").style.display = "none";
      }
  }

  // Payment Submit (Base64 conversion)
  document.getElementById("payment-form").addEventListener("submit", (e) => {
      e.preventDefault();
      if (!currentUser) return alert("Please login first!");

      const tid = document.getElementById("tid-input").value;
      const file = document.getElementById("screenshot-input").files[0];

      if (file) {
          const reader = new FileReader();
          reader.onloadend = async () => {
              try {
                  await setDoc(doc(db, "users", currentUser.uid), {
                      uid: currentUser.uid,
                      name: currentUser.displayName,
                      email: currentUser.email,
                      status: "unpaid",
                      tid: tid,
                      screenshot_base64: reader.result,
                      submitted_at: new Date().toISOString()
                  }, { merge: true });
                  alert("🎉 Details submitted! Waiting for Zeeshan Bhai's approval.");
                  document.getElementById("payment-form").reset();
              } catch (err) { alert("Error: " + err.message); }
          };
          reader.readAsDataURL(file);
      }
  });

  // ================= SECRET TAP LOGIC =================
  let tapCount = 0;
  let tapTimer;

  document.getElementById("secret-trigger").addEventListener("click", () => {
      tapCount++;
      clearTimeout(tapTimer);
      
      // Agar 1 second tak dubara click nahi kiya toh reset ho jaye
      tapTimer = setTimeout(() => { tapCount = 0; }, 1200);

      if (tapCount === 4) {
          tapCount = 0;
          let secretKey = prompt("🔒 Enter Secret Admin Key:");
          if (secretKey === "nor804") {
              openAdminPanel();
          } else if (secretKey !== null) {
              alert("❌ Wrong Secret Key!");
          }
      }
  });

  // Open Admin Panel & Fetch Data
  async function openAdminPanel() {
      document.getElementById("admin-panel").style.display = "flex";
      const listDiv = document.getElementById("student-requests-list");
      listDiv.innerHTML = "<p>Loading pending requests...</p>";

      try {
          const querySnapshot = await getDocs(collection(db, "users"));
          listDiv.innerHTML = "";
          let hasRequests = false;

          querySnapshot.forEach((docSnap) => {
              const data = docSnap.data();
              // Sirf unko dikhao jo unpaid hain aur details bheji hain
              if (data.status === "unpaid" && data.tid) {
                  hasRequests = true;
                  const row = document.createElement("div");
                  row.className = "student-row";
                  row.innerHTML = `
                      <p><strong>Name:</strong> ${data.name || 'Student'}</p>
                      <p><strong>Email:</strong> ${data.email}</p>
                      <p><strong>TID:</strong> <span style="color:red; font-weight:bold;">${data.tid}</span></p>
                      <img src="${data.screenshot_base64}" class="preview-img" alt="Receipt"/>
                      <button class="btn-approve" data-id="${data.uid}">Approve & Unlock</button>
                  `;
                  listDiv.appendChild(row);
              }
          });

          if (!hasRequests) {
              listDiv.innerHTML = "<p style='color:green; font-weight:bold;'>🎉 No pending unpaid requests!</p>";
          }

          // Approve Buttons Click Event
          document.querySelectorAll(".btn-approve").forEach(button => {
              button.addEventListener("click", async (e) => {
                  const studentUid = e.target.getAttribute("data-id");
                  try {
                      await updateDoc(doc(db, "users", studentUid), { status: "paid" });
                      alert("👍 Approved successfully! Course unlocked for this student.");
                      openAdminPanel(); // Refresh list
                      if(currentUser && currentUser.uid === studentUid) checkUserStatus();
                  } catch (err) { alert("Error approving: " + err.message); }
              });
          });

      } catch (err) { listDiv.innerHTML = "<p>Error loading data: " + err.message + "</p>"; }
  }

  // Close Admin Modal
  document.getElementById("close-modal").addEventListener("click", () => {
      document.getElementById("admin-panel").style.display = "none";
  });
</script>
</body>
</html>
