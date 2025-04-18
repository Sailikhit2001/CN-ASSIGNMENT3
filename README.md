git clone https://github.com/StanfordSNR/pantheon.git 

Cd pantheon 

git submodule update --init –recursive 

git clone https://github.com/ravinet/mahimahi.git 

cd mahimahi 

./autogen.sh 

./configure 

make 

sudo make install 

Sudo net.ipv4.ip_forward=1 

mm-delay 50 

Cd 

Cd pantheon 

Python src/wrappers/cubic.py deps 

Python src/wrappers/bbr.py deps 

Python src/wrappers/vegas.py deps 

python src/experiments/setup.py --install-deps --schemes "cubic bbr vegas" 

python src/experiments/setup.py --setup --schemes "cubic bbr vegas" 

python src/experiments/test.py local --schemes "cubic bbr vegas" --data-dir data 

python src/analysis/analyze.py --data-dir data 

PART B 

High bandwidth, low latency (50 Mbps / 10 ms) 

 Create a traces floder in pantheon 

Create a file name 50mbps.trace 

cd ~/pantheon python src/experiments/test.py local  

--schemes "vegas cubic bbr"  

--run-times 1  

--runtime 60  

--data-dir results_50mbps_10ms  

--uplink-trace traces/50mbps.trace  

--downlink-trace traces/50mbps.trace  

--prepend-mm-cmds "mm-delay 5" 

For graphs 

python src/analysis/analyze.py --data-dir results_50mbps_10ms 

 

Low bandwidth, high latency (1 Mbps / 200 ms) 

Create a file name 1mbps.trace 

cd ~/pantheon python src/experiments/test.py local  

--schemes "vegas cubic bbr"  

--run-times 1  

--runtime 60  

--data-dir results_1mbps_200ms  

--uplink-trace traces/1mbps.trace  

--downlink-trace traces/1mbps.trace  

--prepend-mm-cmds "mm-delay 100" 

For graphs 

python src/analysis/analyze.py --data-dir results_1mbps_200ms 

 

 
