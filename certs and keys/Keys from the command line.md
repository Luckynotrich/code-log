1. ssh-keygen -t ed25519  -C rich.rhaskell@gmail.com
			pass phrase: lucky@lucky-Precision-3551

2. chmod 700 ~/.ssh  
  
3. chmod 600 ~/.ssh/*  
  
4. ssh-copy-id -p 7822 richar65@az1-ts106.a2hosting.com
  
5. ssh-agent -s  
  
6. ssh-add ~/.ssh/id_ed25519
