1. wget https://raw.githubusercontent.com/fluent/fluent-bit/master/install.sh 
       -Should work for most Linux flavors, if not use - https://docs.fluentbit.io/manual/installation/getting-started-with-fluent-bit 

Note: Fluent-bit.conf & parsers.conf will likely be installed in /etc/fluent-bit 

2. Replace fluent-bit.conf with the provided .conf (fluent-bit-linux.conf) and fill in the missing values below
    -Authorization Token -> You can find this token in the portal -> top right user icon -> License -> Account - Ingest Token 
    -Machine_Name -> Replace this with the name of your machine. This will help later when IDing the metrics.
    -[Input] Path -> replace PATH_TO_BOOMI_ATOM_HERE with the path leading up to Boomi_AtomSphere/

3. Replace the parsers.conf with the provided parser (parsers.conf)
    -No values to be filled in here

4. Navigate to where your fluent-bit executable is (likely /opt/fluent-bit/bin)
     -Run this command: ./fluent-bit -c PATH_TO_FLUENT_BIT_CONF/fluent-bit.conf

5. Go to your ADF instance -> Explore -> Logs & Insights -> bottom of page should have your Machine Name & App Name -> Click on your app name -> logs here

