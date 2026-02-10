# Server Management Commands

## Problem: Port 3000 Already in Use

Agar aap terminal close kar dete ho lekin server background mein chal raha ho, to port 3000 already in use error aata hai.

## Check Server Status & Port

### Server kis port par chal raha hai check karne ke liye:

```bash
# Quick check (recommended)
npm run status

# Detailed check with process info
npm run check-port

# Manual check - Port 3000 check karo
lsof -i:3000

# All ports check karo
lsof -i -P -n | grep LISTEN

# Specific port check (3000 ki jagah koi bhi port)
lsof -i:3000
```

## Solutions:

### Option 1: Use npm scripts (Recommended)
```bash
# Server stop karne ke liye
npm run stop

# Server restart karne ke liye (stop + start)
npm run restart

# Server start karne ke liye
npm run start:dev
```

### Option 2: Manual kill command
```bash
# Port 3000 par running process ko kill karo
lsof -ti:3000 | xargs kill -9

# Phir server start karo
npm run start:dev
```

### Option 3: Use kill script
```bash
# Script use karo
./kill-server.sh

# Phir server start karo
npm run start:dev
```

## Important Notes:

1. **Terminal close karne se server kill nahi hota** - Background processes continue running
2. **Always stop server before starting** - Use `npm run stop` first
3. **Use `npm run restart`** - This automatically stops and starts the server

## Quick Commands:

```bash
# Check server status (quick)
npm run status

# Check server status (detailed)
npm run check-port

# Stop server
npm run stop

# Start server in development mode
npm run start:dev

# Restart server (stop + start)
npm run restart
```

## Server Port Information:

**Default Port:** 3000 (as defined in `src/main.ts`)

Agar aap port change karna chahte ho:
1. `.env` file mein `PORT=3001` add karo
2. Ya `src/main.ts` mein directly change karo: `const port = process.env.PORT || 3001;`

