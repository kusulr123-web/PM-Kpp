<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ASH POND PUMP A - KPP-F-EM-101</title>
    <style>
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background-color: #eef2f5; color: #333; margin: 0; padding: 20px; }
        .container { max-width: 1000px; margin: auto; background: #fff; padding: 30px; border-radius: 8px; box-shadow: 0 4px 15px rgba(0,0,0,0.1); }
        .header { text-align: center; border-bottom: 3px solid #2c3e50; padding-bottom: 15px; margin-bottom: 25px; }
        .header img { width: 130px; height: auto; margin-bottom: 15px; }
        .header h1 { margin: 0; color: #2c3e50; font-size: 24px; }
        .header p { margin: 5px 0 0; color: #7f8c8d; font-weight: bold; }
        h3 { color: #fff; background-color: #34495e; padding: 10px 15px; border-radius: 4px; font-size: 16px; margin-top: 30px; }
        
        .toggle-btn { background-color: #2980b9; color: white; font-size: 16px; font-weight: bold; padding: 15px; width: 100%; border: none; border-radius: 4px; cursor: pointer; margin-top: 10px; margin-bottom: 10px; transition: background 0.3s; display: flex; justify-content: space-between; align-items: center; }
        .toggle-btn:hover { background-color: #1f6391; }
        
        .status-list-container { max-width: 800px; margin: 0 auto 30px auto; text-align: left; }
        .list-item-row { display: flex; justify-content: space-between; align-items: center; background: #fff; padding: 14px 20px; border-radius: 6px; margin-bottom: 10px; border: 1px solid #e2e8f0; box-shadow: 0 2px 4px rgba(0,0,0,0.02); }
        .item-title { font-size: 15px; color: #2c3e50; font-weight: bold; flex: 1; }
        .item-status { margin: 0 20px; }
        .item-time { font-size: 14px; color: #34495e; font-weight: bold; min-width: 170px; text-align: right; }
        
        .status-badge { display: inline-block; padding: 4px 10px; border-radius: 12px; font-size: 12px; font-weight: bold; color: white; text-align: center; }
        .status-ok { background-color: #2ecc71; }    
        .status-miss { background-color: #e74c3c; }  
        .status-none { background-color: #95a5a6; }  
        
        .grid-2 { display: grid; grid-template-columns: 1fr 1fr; gap: 15px; }
        .grid-3 { display: grid; grid-template-columns: repeat(3, 1fr); gap: 15px; }
        .grid-4 { display: grid; grid-template-columns: repeat(4, 1fr); gap: 15px; }
        .form-group { margin-bottom: 10px; }
        label { display: block; font-weight: 600; margin-bottom: 5px; font-size: 13px; color: #444; }
        input[type="text"], input[type="date"], select { width: 100%; padding: 8px 10px; border: 1px solid #ccc; border-radius: 4px; box-sizing: border-box; font-size: 14px; transition: 0.3s; }
        input[type="text"]:focus, select:focus { border-color: #3498db; outline: none; }
        .vibration-container { background: #f8f9fa; padding: 15px; border: 1px solid #ddd; border-radius: 4px; }
        .submit-btn { background-color: #27ae60; color: white; font-size: 18px; font-weight: bold; padding: 15px; width: 100%; border: none; border-radius: 4px; cursor: pointer; margin-top: 35px; transition: background 0.3s; }
        .submit-btn:hover { background-color: #219150; }
        .top-section { background-color: #f8f9fa; padding: 15px 20px; border-left: 4px solid #3498db; border-radius: 4px; margin-bottom: 20px; display: grid; grid-template-columns: 1fr 1fr; gap: 20px; }
        
        #summaryPage { display: none; text-align: center; padding: 20px; animation: fadeIn 0.4s ease-out; }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
        .check-icon-large { background: #2ecc71; color: white; width: 80px; height: 80px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 45px; margin: 0 auto 15px auto; box-shadow: 0 4px 10px rgba(46, 204, 113, 0.4); }
        #summaryPage h2 { color: #2c3e50; font-size: 26px; margin-bottom: 20px; }
        
        .current-save-box { background: #f8f9fa; border: 2px solid #e2e8f0; padding: 20px; border-radius: 8px; text-align: left; max-width: 800px; margin: 0 auto 30px auto; box-shadow: 0 2px 5px rgba(0,0,0,0.02); }
        .current-save-box .info-line { font-size: 15px; margin-bottom: 8px; color: #34495e; }
        .current-save-box .info-line:last-child { margin-bottom: 0; }
        .current-save-box b { color: #2c3e50; }

        .summary-dashboard-title { text-align: left; font-size: 17px; color: #2980b9; border-bottom: 2px solid #bdc3c7; padding-bottom: 10px; margin-bottom: 20px; font-weight: bold; max-width: 800px; margin-left: auto; margin-right: auto; margin-top: 10px;}
        .done-btn { background: #3498db; color: #fff; border: none; padding: 15px 40px; font-size: 18px; font-weight: bold; border-radius: 6px; cursor: pointer; width: 100%; max-width: 800px; transition: background 0.3s; margin-top: 20px; }
        .done-btn:hover { background: #2980b9; }

        @media screen and (max-width: 768px) { 
            body { padding: 10px; } .container { padding: 15px; } .header img { width: 100px; } .header h1 { font-size: 20px; } 
            .top-section, .grid-2, .grid-3, .grid-4 { grid-template-columns: 1fr; gap: 10px; } 
            .list-item-row { flex-direction: column; align-items: flex-start; padding: 12px 15px; }
            .item-status { margin: 6px 0; }
            .item-time { text-align: left; width: 100%; border-top: 1px dashed #e2e8f0; padding-top: 8px; margin-top: 4px; color: #2980b9; }
        }
    </style>
</head>
<body>
<div class="container">
    <div class="header">
        <img src="https://i.postimg.cc/PrC0NcRN/logo-kpp.png" alt="KPP Logo">
        <h1>KHONBURI POWER PLANT</h1>
        <p>ASH POND PUMP CHECK (KPP-F-EM-101)</p>
    </div>

    <div id="mainFormArea">
        <button type="button" id="toggleDashBtn" class="toggle-btn" onclick="toggleDashboard()">
            <span>📊 สถานะการตรวจเช็คทั้งหมด (ASH POND)</span>
            <span id="toggleIcon">🔽 กดเพื่อดู</span>
        </button>
        <div id="dashboardContainer" style="display: none;">
            <div class="status-list-container" id="dashboardGrid"></div>
        </div>

        <h3 style="background-color: #34495e;">📝 ฟอร์มบันทึกข้อมูล (เครื่องที่กำลังตรวจ)</h3>
        <form id="pumpPmForm">
            
            <div style="background-color: #fffaf0; border: 2px dashed #f39c12; padding: 15px; border-radius: 6px; margin-bottom: 20px;">
                <label style="font-size: 16px; color: #d35400; font-weight: bold; margin-bottom: 8px;">⚙️ สถานะเครื่องจักรปัจจุบัน:</label>
                <select id="machineStatusToggle" onchange="handleMachineStatus()" style="font-size: 16px; font-weight: bold; color: #2c3e50; border-color: #f39c12; background-color: #fff;">
                    <option value="Running">🟢 กำลังเดินเครื่อง (Running)</option>
                    <option value="Standby">🟡 ไม่ได้เดินเครื่อง / Standby (Stop)</option>
                    <option value="Maintenance">🛠️ อยู่ระหว่างซ่อมแซม (Maintenance)</option>
                </select>
            </div>

            <div class="top-section">
                <div class="form-group" style="margin-bottom: 0;">
                    <label style="font-size: 15px; color: #2c3e50;">วันที่ตรวจเช็ค (DATE):</label>
                    <input type="date" name="date" required id="dateInput">
                </div>
                <div class="form-group" style="margin-bottom: 0;">
                    <label style="font-size: 15px; color: #2c3e50;">เครื่องจักรที่กำลังตรวจ:</label>
                    <div id="machineLabel" style="padding: 8px 10px; background: #e8f0fe; border-radius: 4px; font-weight: bold; color: #2980b9; font-size: 15px; border: 1px solid #b3d4fc;">
                        ASH POND PUMP NO. A
                    </div>
                    <input type="hidden" name="targetSheet" value="Ash pond no.A">
                </div>
            </div>

            <div class="grid-2">
                <div class="form-group"><label>1. Lubricant Level (ระดับสารหล่อลื่น):</label><select name="lubeLevel" class="lockable-select"><option value="In Range">In Range (ปกติ)</option><option value="Low">Low (ต่ำ)</option><option value="High">High (สูง)</option><option value="-">- (Standby/Repair)</option></select></div>
                <div class="form-group"><label>2. Check Leakage (การรั่วซึม):</label><select name="leakage" class="lockable-select"><option value="No leak">No leak (ไม่รั่ว)</option><option value="Leak">Leak (รั่ว)</option><option value="-">- (Standby/Repair)</option></select></div>
                <div class="form-group"><label>3. Overall Condition (สภาพทั่วไป):</label><select name="overallCond" class="lockable-select"><option value="Good">Good (ปกติ)</option><option value="Abnormal">Abnormal (ผิดปกติ)</option><option value="-">- (Standby/Repair)</option></select></div>
                <div class="form-group"><label>4. Abnormal noise (DE):</label><select name="noiseDe" class="lockable-select"><option value="Nor ">Normal (ปกติ)</option><option value="Abnor">Abnormal (ผิดปกติ)</option><option value="-">- (Standby/Repair)</option></select></div>
                <div class="form-group"><label>5. Abnormal noise (NDE):</label><select name="noiseNde" class="lockable-select"><option value="Nor">Normal (ปกติ)</option><option value="Abnor">Abnormal (ผิดปกติ)</option><option value="-">- (Standby/Repair)</option></select></div>
            </div>

            <h3 style="margin-top: 15px;">ค่าพารามิเตอร์การทำงาน (Operating Parameters)</h3>
            <div class="grid-4">
                <div class="form-group"><label>Pressure Suction (Bar):</label><input type="text" inputmode="decimal" name="pressSuction" class="lockable-input"></div>
                <div class="form-group"><label>Pressure Discharge (Bar):</label><input type="text" inputmode="decimal" name="pressDischarge" class="lockable-input"></div>
                <div class="form-group"><label>Bearing Temp. DE (°C):</label><input type="text" inputmode="decimal" name="tempDe" class="lockable-input"></div>
                <div class="form-group"><label>Bearing Temp. NDE (°C):</label><input type="text" inputmode="decimal" name="tempNde" class="lockable-input"></div>
            </div>

            <h3 style="margin-top: 15px;">การวัดค่าความสั่นสะเทือน (Vibration)</h3>
            <div class="vibration-container">
                <label style="color:#c0392b; font-size:14px; margin-bottom: 15px; display:block; font-weight: bold;">Vibration Max = 4.5 mm/s</label>
                <div class="grid-3">
                    <div class="form-group"><label>DE - H:</label><input type="text" inputmode="decimal" name="vibDeH" class="lockable-input"></div>
                    <div class="form-group"><label>DE - V:</label><input type="text" inputmode="decimal" name="vibDeV" class="lockable-input"></div>
                    <div class="form-group"><label>DE - A:</label><input type="text" inputmode="decimal" name="vibDeA" class="lockable-input"></div>
                </div>
                <div class="grid-3" style="margin-top: 10px;">
                    <div class="form-group"><label>NDE - H:</label><input type="text" inputmode="decimal" name="vibNdeH" class="lockable-input"></div>
                    <div class="form-group"><label>NDE - V:</label><input type="text" inputmode="decimal" name="vibNdeV" class="lockable-input"></div>
                    <div class="form-group"><label>NDE - A:</label><input type="text" inputmode="decimal" name="vibNdeA" class="lockable-input"></div>
                </div>
            </div>

            <h3 style="margin-top: 15px;">สรุปผลและการรับรอง</h3>
            <div class="grid-3">
                <div class="form-group"><label>Inspected By (ผู้ตรวจสอบ):</label><input type="text" name="inspectedBy" id="inspectedByInput" required></div>
                <div class="form-group"><label>Approved By (ผู้อนุมัติ):</label><input type="text" name="approvedBy" id="approvedByInput"></div>
                <div class="form-group"><label>Remarks (หมายเหตุ):</label><input type="text" name="remarks" id="remarksInput"></div>
            </div>

            <button type="submit" class="submit-btn" id="submitBtn">บันทึกข้อมูล PM ลงระบบ</button>
        </form>
    </div>

    <div id="summaryPage">
        <div class="check-icon-large">✓</div>
        <h2>บันทึกข้อมูลสำเร็จ!</h2>
        
        <div class="current-save-box">
            <div class="info-line"><b>⚙️ เครื่องจักรที่บันทึก:</b> <span id="sumMachineText" style="color:#2980b9; font-weight:bold;"></span></div>
            <div class="info-line"><b>📅 วันที่ตรวจเช็ค:</b> <span id="sumDateText"></span></div>
            <div class="info-line"><b>⏰ เวลาที่บันทึกลงระบบ:</b> <span id="sumTimeText" style="color:#27ae60; font-weight:bold;"></span></div>
        </div>

        <div class="summary-dashboard-title">
            📋 Status รายวันและเวลาของทุกเครื่อง (รีเซ็ตสัปดาห์ละครั้ง คืนวันอาทิตย์ 23:59 น.)
        </div>
        
        <div class="status-list-container" id="summaryDashboardGrid"></div>

        <button class="done-btn" onclick="window.location.reload()">ตกลงและตรวจเช็คเครื่องถัดไป</button>
    </div>
</div>

<script>
    const scriptURL = 'https://script.google.com/macros/s/AKfycbycZaIagbcjqp-dSV5GJrWfsBux4JCbU5z85eaV2ztPFriIKp_a7JL-oqH0UMp1_gxX/exec'; 
    
    document.getElementById('dateInput').valueAsDate = new Date();

    const targetSheetNames = [
        "Ash pond no.A", "Ash pond B", "Ash pond C",
        "Ash pond d", "Ash pond E", "Ash pond F",
        "Ash pond G", "Ash pond H"
    ];

    window.addEventListener('DOMContentLoaded', () => {
        renderLocalDashboard('dashboardGrid');
        
        const savedInspector = localStorage.getItem('saved_inspectedBy');
        const savedApprover = localStorage.getItem('saved_approvedBy');
        if (savedInspector) document.getElementById('inspectedByInput').value = savedInspector;
        if (savedApprover) document.getElementById('approvedByInput').value = savedApprover;
    });

    // 🌟 ปรับปรุงฟังก์ชันสลับสถานะเพื่อรองรับโหมด "ซ่อมแซม (Maintenance)"
    function handleMachineStatus() {
        const status = document.getElementById('machineStatusToggle').value;
        const lockableInputs = document.querySelectorAll('.lockable-input');
        const lockableSelects = document.querySelectorAll('.lockable-select');
        const remarksInput = document.getElementById('remarksInput');

        if (status === 'Standby' || status === 'Maintenance') {
            lockableInputs.forEach(input => {
                input.disabled = true; 
                input.style.backgroundColor = '#e9ecef'; 
                input.value = '-'; 
            });
            lockableSelects.forEach(select => {
                select.disabled = true;
                select.style.backgroundColor = '#e9ecef';
                select.value = '-';
            });
            
            // ปรับข้อความหมายเหตุตามสถานะจริง
            if (status === 'Standby') {
                remarksInput.value = 'Standby (ไม่ได้เดินเครื่อง)';
            } else {
                remarksInput.value = 'อยู่ระหว่างซ่อมแซม (Maintenance)';
            }
        } else {
            lockableInputs.forEach(input => {
                input.disabled = false; 
                input.style.backgroundColor = '#fff'; 
                input.value = ''; 
            });
            lockableSelects.forEach(select => {
                select.disabled = false;
                select.style.backgroundColor = '#fff';
                select.selectedIndex = 0; 
            });
            if(remarksInput.value === 'Standby (ไม่ได้เดินเครื่อง)' || remarksInput.value === 'อยู่ระหว่างซ่อมแซม (Maintenance)') {
                remarksInput.value = ''; 
            }
        }
    }

    function toggleDashboard() {
        const container = document.getElementById('dashboardContainer');
        const icon = document.getElementById('toggleIcon');
        if (container.style.display === 'none') {
            container.style.display = 'block';
            icon.innerText = '🔼 กดเพื่อซ่อน';
        } else {
            container.style.display = 'none';
            icon.innerText = '🔽 กดเพื่อดู';
        }
    }

    function getLastResetDeadline() {
        let now = new Date();
        let deadline = new Date(now);
        let day = now.getDay(); 
        deadline.setDate(now.getDate() - day);
        deadline.setHours(23, 59, 0, 0); 
        if (now < deadline) {
            deadline.setDate(deadline.getDate() - 7);
        }
        return deadline.getTime();
    }

    function renderLocalDashboard(gridId) {
        const grid = document.getElementById(gridId);
        grid.innerHTML = ''; 
        let lastResetTime = getLastResetDeadline();
        
        targetSheetNames.forEach((sheetName, index) => {
            let statusClass = "status-none", statusText = "ไม่มีข้อมูล";
            let displayTime = "ยังไม่ได้ทำการตรวจเช็ค";

            let localTime = localStorage.getItem(`pump_time_${sheetName}`);
            let localTimestamp = localStorage.getItem(`pump_timestamp_${sheetName}`);

            if (localTimestamp) {
                if (parseInt(localTimestamp) < lastResetTime) {
                    localStorage.removeItem(`pump_time_${sheetName}`);
                    localStorage.removeItem(`pump_timestamp_${sheetName}`);
                    localTime = null;
                    localTimestamp = null;
                }
            }

            if (localTime) {
                statusClass = "status-ok";
                statusText = "✅ ตรวจแล้ว";
                displayTime = localTime;
            }

            let fullName = "ASH POND PUMP NO. " + sheetName.replace(/Ash pond no\./i, "").replace(/Ash pond /i, "").toUpperCase().trim();
            grid.innerHTML += `
                <div class="list-item-row">
                    <div class="item-title">ข้อ ${index + 1}. ${fullName}</div>
                    <div class="item-status">
                        <span class="status-badge ${statusClass}">${statusText}</span>
                    </div>
                    <div class="item-time">🕒 ${displayTime}</div>
                </div>
            `;
        });
    }

    const form = document.getElementById('pumpPmForm');
    const btn = document.getElementById('submitBtn');

    form.addEventListener('submit', e => {
        e.preventDefault(); 
        btn.innerHTML = 'กำลังบันทึกข้อมูล... ⏳'; btn.style.backgroundColor = '#f39c12'; btn.disabled = true;
        
        const lockableInputs = document.querySelectorAll('.lockable-input');
        const lockableSelects = document.querySelectorAll('.lockable-select');
        lockableInputs.forEach(input => input.disabled = false);
        lockableSelects.forEach(select => select.disabled = false);

        const formData = new FormData(form);
        const rawDate = formData.get('date');
        const currentSheet = formData.get('targetSheet'); 
        const inspectorValue = formData.get('inspectedBy');
        const approvedByValue = formData.get('approvedBy');
        let displayDateForUI = rawDate; 
        
        if (inspectorValue) localStorage.setItem('saved_inspectedBy', inspectorValue);
        if (approvedByValue) localStorage.setItem('saved_approvedBy', approvedByValue);

        if (rawDate) {
            const months = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];
            const parts = rawDate.split('-'); 
            const formattedDate = `${parts[2]}-${months[parseInt(parts[1], 10) - 1]}-${parts[0]}`; 
            formData.set('date', formattedDate); 
            displayDateForUI = `${parts[2]}/${parts[1]}/${parts[0]}`;
        }

        const now = new Date();
        const timeStr = String(now.getHours()).padStart(2, '0') + ':' + String(now.getMinutes()).padStart(2, '0');
        const finalLocalTimeStr = `${displayDateForUI} | ${timeStr} น.`;

        localStorage.setItem(`pump_time_${currentSheet}`, finalLocalTimeStr);
        localStorage.setItem(`pump_timestamp_${currentSheet}`, now.getTime());

        fetch(scriptURL, { method: 'POST', body: formData, mode: 'no-cors' })
            .then(response => { 
                document.getElementById('mainFormArea').style.display = 'none';
                document.getElementById('summaryPage').style.display = 'block';
                window.scrollTo(0, 0); 
                
                document.getElementById('sumMachineText').innerText = document.getElementById('machineLabel').innerText;
                document.getElementById('sumDateText').innerText = displayDateForUI;
                document.getElementById('sumTimeText').innerText = timeStr + ' น.';
                
                renderLocalDashboard('summaryDashboardGrid');
            })
            .catch(error => { 
                alert('เกิดข้อผิดพลาดในการเชื่อมต่อระบบอินเทอร์เน็ต: ' + error.message); 
                btn.innerHTML = 'บันทึกข้อมูล PM ลงระบบ'; btn.style.backgroundColor = '#27ae60'; btn.disabled = false; 
            });
    });
</script>
</body>
</html>
