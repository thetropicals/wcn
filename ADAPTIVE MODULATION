clc; clear; close all;
s=randi([0,1],1,1000);
error=[];
op=[];
v=1/length(s);
for snr=1:30
    if snr>=0 && snr<=13
        x=pskmod(s,2)
    end
    if snr>=13 && snr<=20
        x=pskmod(s,4)
    end
    if snr>=20 && snr<=26
        x=qammod(s,16)
    end
    if snr>=26 && snr<=30
        x=qammod(s,64)
    end
    y=awgn(x,snr)

    if snr>=0 && snr<=13
        dm=pskdemod(y,2)
    end
    if snr>=13 && snr<=20
        dm=pskdemod(y,4)
    end
    if snr>=20 && snr<=26
        dm=qamdemod(y,16)
    end
    if snr>=26 && snr<=30
        dm=qamdemod (y,64)
    end
    [num,rat]=biterr(s,dm);
    if rat==0
       rat=v;
    end
    error=[error rat];
end 
subplot(2,1,1)
semilogy(0:29,error)
throughput=[];
for i =1:30
    if i>=0 && i<13
        throughput= [throughput 1];
        disp(throughput);
    end;
    if i>=13 && i<20
        throughput= [throughput 2];
        disp(throughput);
    end;
    if i>=20 && i<26
        throughput= [throughput 4];
        disp(throughput);
    end;
    if i>=26 && i<=30
        throughput= [throughput 6];
        disp(throughput);
    end
end
subplot(2,1,2);
semilogy(0:29,throughput)
