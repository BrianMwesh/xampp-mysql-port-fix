# XAMPP MySQL Port 3306 Error Fix

## Problem

When starting MySQL in XAMPP, the following error appears:

- Port 3306 in use
- MySQL WILL NOT start without the configured ports free
- Unable to open process

This happens because another application is already using port 3306.

---

## Cause

Port 3306 is the default MySQL port. Common causes include:

- MySQL Server installed separately
- MariaDB running as a Windows service
- Another XAMPP instance
- Background database service using the same port

---

## Solution 1: Stop the Service Using Port 3306

1. Press `Win + R`
2. Type `services.msc`
3. Look for:
   - MySQL
   - MySQL80
   - MariaDB
4. Right-click → Stop

Then restart MySQL in XAMPP.

---

## Solution 2: Change MySQL Port in XAMPP

### Step 1: Change MySQL Port

1. Open XAMPP
2. Click Config (next to MySQL)
3. Open `my.ini`
4. Change:

```
port=3306
```

to:

```
port=3307
```

Save the file.

---

### Step 2: Update phpMyAdmin

1. Open `config.inc.php`
2. Change:

```
$cfg['Servers'][$i]['port'] = '3306';
```

to:

```
$cfg['Servers'][$i]['port'] = '3307';
```

Save the file.

---

## Solution 3: Check Using Command Prompt

Run:

```
netstat -ano | findstr :3306
```

Then identify the process using:

```
tasklist | findstr PID_NUMBER
```

---

## Result

After stopping the conflicting service or changing the port, MySQL should start successfully in XAMPP.


