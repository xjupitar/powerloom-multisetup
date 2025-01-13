# Powerloom Multisetup
## Step 1: Update your server. 
<pre><code>sudo apt update</code></pre>
<pre><code>sudo apt upgrade</code></pre>
Type Y if asked. 
## Step 2: Install Screen
<pre><code>sudo apt install screen</code></pre>
## Step 3: Install Python
Check if python is installed
<pre><code>python3 --version</code></pre>
If intalled you're good to go. If not, intsall python using following command
<pre><code>sudo apt install python3</code></pre>
## Step 4: Install Docker
Check if docker is installed using 
<pre><code>docker --version</code></pre>
If intalled you're good to go. If not, intsall docker using following command
<pre><code>sudo apt install docker.io</code></pre>
## Step 5: Install Docker Compose
<pre><code>sudo apt-get update
sudo apt-get install ca-certificates curl 
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc</code></pre>
Add the repository to Apt sources
<pre><code>echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
$(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update</code></pre>
install docker components
<pre><code>sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin</code></pre>
Type Y if asked.
## Step 6: Clone the repository
<pre><code>git clone https://github.com/PowerLoom/snapshotter-lite-multi-setup
cd snapshotter-lite-multi-setup</code></pre>
## Step 7: Install Pyenv
<pre><code>sudo apt install build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev curl libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev</code></pre>
Type Y when asked.
## Step 8: Run Pyenv installation package
<pre><code>curl https://pyenv.run | bash</code></pre>
## Step 9: Edit pyenv
<pre><code>nano ~/.bashrc</code></pre>
Inside the nano editor, add the following lines at the end of the file:
<pre><code>export PATH="$HOME/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"</code></pre>
To save the nano file, use CTRL+X and then hit enter.
Refresh the terminal by typing:
<pre><code>source ~/.bashrc</code></pre>
Next, proceed to install Python 3.11.5
<pre><code>pyenv install 3.11.5</code></pre>
## Step 10: Intall pyenv virtual
<pre><code>echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.bashrc
pyenv virtualenv 3.11.5 ss_lite_multi_311
pyenv local ss_lite_multi_311</code></pre>
## Step 11: Setup node
To establish a multi-node setup, fisrt create a env file using
<pre><code>./bootstrap.sh</code></pre>
Now please enter your Wallet holder adderss, Source RPC url, Signer address, signer address private key accordingly. <br>
**Note: <br>
Wallet Holder address is your slot address/node license address <br>
Signer address is your burner address that you set in the Snapshotter dashboard.**<br>
Now install python requirements
<pre><code>pip install -r requirements.txt</code></pre>
Execute the setup
<pre><code>python multi_clone.py</code></pre>
Do you want to deploy all slots? Type Y and hit enter <br>
Select data market (For Aave type 1 and hit enter, for Uniswap type 2 and hit enter<br>

## Check Diagnose 
<pre><code>./diagnose.sh</code></pre>

## Some Tips
<br>
If you see docker deamon in not running after using diagnose, use this command
<pre><code>sudo systemctl start docker</code></pre>
Then use diagnose command again
<pre><code>./diagnose.sh</code></pre>
After that delete all derectories and screens by typing Y. <br>
This will delete all your slots <br>
Now start the python script again to run the node
<pre><code>python multi_clone.py</code></pre>
Refresh your Shapshotter Dashboard to check if all slots working.
