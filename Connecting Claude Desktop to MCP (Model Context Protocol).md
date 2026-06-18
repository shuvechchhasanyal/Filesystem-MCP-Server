# **Connecting Claude Desktop to MCP (Model Context Protocol)**

## **Overview**

This guide explains how to connect Claude Desktop to an MCP (Model Context Protocol) server, enabling Claude to access and interact with files on your local machine.

In this example, we will configure the Filesystem MCP Server so Claude can access files stored in the Desktop and Downloads folders.

---

## **Prerequisites**

Before proceeding, ensure the following are installed:

1. **Claude Desktop**  
2. **Cursor** (optional but useful for editing configuration files)  
3. **Node.js** and **npm** installed on your system

---

## **Step 1: Install Claude Desktop**

Download and install Claude Desktop on your machine.

After installation, launch Claude Desktop once to ensure all configuration files are created.

---

## **Step 2: Install Cursor**

Download and install Cursor.

Cursor can be used to easily edit Claude Desktop configuration files and manage MCP-related settings.

---

## **Step 3: Open Claude Desktop Configuration**

1. Launch Claude Desktop.  
2. Navigate to:  
   **Settings → Developer**  
3. Click **Edit Config**.

This opens the `config.json` file used by Claude Desktop.

---

## **Step 4: Configure the Filesystem MCP Server**

Add the following configuration to the `config.json` file:

{  
  "mcpServers": {  
    "filesystem": {  
      "command": "npx",  
      "args": \[  
        "-y",  
        "@modelcontextprotocol/server-filesystem",  
        "/Users/username/Desktop",  
        "/Users/username/Downloads"  
      \]  
    }  
  }  
}

### **Important**

Replace:

username

with your macOS username.

For example:

{  
  "mcpServers": {  
    "filesystem": {  
      "command": "npx",  
      "args": \[  
        "-y",  
        "@modelcontextprotocol/server-filesystem",  
        "/Users/john/Desktop",  
        "/Users/john/Downloads"  
      \]  
    }  
  }  
}

---

## **Step 5: Save and Restart Claude**

1. Save the `config.json` file.  
2. Completely close Claude Desktop.  
3. Reopen Claude Desktop.

During startup, Claude will automatically launch and connect to the configured MCP server.

---

## **Step 6: Verify the Connection**

Open a new Claude conversation and ask Claude to perform actions involving files in the configured directories.

Examples:

* "List the files in my Downloads folder."  
* "Read the PDF on my Desktop and summarize it."  
* "Create a text file in Downloads containing today's notes."  
* "Find all CSV files in my Desktop folder."

If the configuration is successful, Claude will automatically use the filesystem MCP tool to access and interact with the permitted folders.

---

## **What Claude Can Do**

Once connected to the Filesystem MCP Server, Claude can:

* Read files  
* Search folders  
* Create new files  
* Modify existing files  
* Organize documents  
* Analyze local datasets  
* Summarize PDFs and text files  
* Generate code and save it directly to your machine

### **Access Restrictions**

Claude can only access the directories explicitly specified in the configuration:

/Users/\<username\>/Desktop  
/Users/\<username\>/Downloads

Any folders not listed in the configuration remain inaccessible.

---

## **Troubleshooting**

### **MCP Server Not Appearing**

Verify Node.js is installed:  
node \--version  
npm \--version

*   
* Ensure the JSON syntax is valid.  
* Restart Claude Desktop after making configuration changes.

### **Permission Issues**

* Confirm the folder paths are correct.  
* Ensure Claude Desktop has permission to access the specified directories.

### **Server Fails to Start**

Run the MCP server manually to verify installation:

npx \-y @modelcontextprotocol/server-filesystem

If errors occur, reinstall Node.js and try again.

---

## **Summary**

By configuring the Filesystem MCP Server in Claude Desktop, Claude gains controlled access to selected local folders. This allows Claude to work directly with files stored on your machine, enabling document analysis, file management, code generation, and other local workflows while remaining restricted to the directories you explicitly authorize.

