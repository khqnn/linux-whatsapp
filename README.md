# linux-whatsapp

Using **Nativefier** to create a standalone WhatsApp application on Ubuntu is a straightforward process. Nativefier allows you to turn any web app into a desktop application.

<div id="techpurview-img" align="center">
  <img width="1785" alt="303564370-41c0c3d3-4803-451e-9df9-8acb20fd2908" src="https://github.com/user-attachments/assets/d2fd9347-181d-4397-abea-2e69c834c343">
</div>

1. **Install Node.js and npm**

   Nativefier requires Node.js and npm (Node Package Manager). Install them using the following commands:

   ```bash
   sudo apt update
   sudo apt install nodejs npm
   ```

   Verify the installation with:

   ```bash
   node -v
   npm -v
   ```
2. **Install Nativefier**

   Use npm to install Nativefier globally:

   ```bash
   sudo npm install -g nativefier
   ```

   Verify the installation with:

   ```bash
   nativefier --version

3. **Create the WhatsApp App**

   Use Nativefier to create a standalone app for WhatsApp Web. Open a terminal and run:

   ```bash
   nativefier --name "WhatsApp" "https://web.whatsapp.com/"
   ```

   This command does the following:
   - `--name "WhatsApp"`: Specifies the name of the application.
   - `"https://web.whatsapp.com/"`: URL of the web app you want to package.

4. **Locate the Application**

   Nativefier will create a directory with the application files in your current working directory. You can navigate to this directory using:

   ```bash
   cd WhatsApp-linux-x64
   ```

5. **Run the Application**

   Inside the directory, you’ll find an executable file. Run it with:

   ```bash
   ./WhatsApp
   ```

   If you encounter permission issues, you may need to make the file executable:
   ```bash
   chmod +x WhatsApp
   ```
   If the `chrome-sandbox` binary doesn’t have the correct permissions or ownership you can do the following:
   navigate to the folder
   ```bash
   cd /path/to/your/WhatsApp/WhatsApp-linux-x64
   ```

   You need to change the ownership of the `chrome-sandbox` file to root:

   ```bash
   sudo chown root:root chrome-sandbox
   ```

   Set the `chrome-sandbox` binary to have the SUID bit set (this is required for sandboxing to work correctly):

   ```bash
   sudo chmod 4755 chrome-sandbox
   ```

   Try running the application again:

   ```bash
   ./WhatsApp
   ```


6. **Create a Desktop Shortcut (Optional)**

   To make it easier to access the WhatsApp app, you can create a desktop shortcut:

   - Create a `.desktop` file in `~/.local/share/applications/`:

     ```bash
     nano ~/.local/share/applications/whatsapp.desktop
     ```

   - Add the following content to the file:

     ```ini
     [Desktop Entry]
     Name=WhatsApp
     Comment=WhatsApp Web as a standalone app
     Exec=/path/to/your/WhatsApp-linux-x64/WhatsApp
     Icon=/path/to/your/WhatsApp-linux-x64/resources/app/icon.png
     Terminal=false
     Type=Application
     Categories=Utility;
     ```

     Replace `/path/to/your/WhatsApp-linux-x64/WhatsApp` with the actual path to the executable, and update the `Icon` path if needed.

   - Save the file and exit the editor (`Ctrl+X`, then `Y`, then `Enter`).

   - You should now see WhatsApp in your applications menu, and you can drag it to your dock or launcher for easy access.
