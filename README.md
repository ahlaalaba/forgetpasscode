# 1. Create a folder for your website and open it
mkdir my-website
cd my-website

# 2. Initialize a local Git repository
git init -b main

# 3. Create your website's home page (it must be named index.html)
echo "<h1>Welcome to my Git-powered website!</h1>" > index.html

# 4. Link your local folder to your GitHub repository
# (Replace with your actual GitHub URL)
git remote add origin https://github.com

# 5. Stage, commit, and push your code
git add .
git commit -m "Initial commit: added index.html"
git push -u origin main
