RHEL 8 Virtualization:
----------------------------------;
 => virt-manager (GUI interface)/Virsh (CLI)
 => libvirt (daemon + API collection)
 => qemu-kvm (emulator for virtual OS)
প্রথমে চেক করে নিতে হবে যে, আমাদের এই পিসি/ল্যাপটপ/সার্ভারে ব্যবহৃত প্রসেসর টি Virtualization সাপোর্ট করে কিনা। এর জন্য টার্মিনাল থেকে নিচের কমান্ডটি দিতে হবে। এখানে বলে রাখা ভালো যে আপনার প্রসেসর যদি Intel হয় তাহলে এক কমান্ডহবে আর যদি AMD হয় তাহলে অন্য কমান্ড হবে।  
Step 01: Check VT Support:
---------------------------------------------
[root@hostX ~]# grep -i vmx /proc/cpuinfo      ; প্রসেসর যদি Intel হয়।
[root@hostX ~]# grep -i svm /proc/cpuinfo      ; প্রসেসর যদি AMD হয়। 
প্রসেসর এবং মেমরি (RAM) সম্পর্কিত তথ্য পাওয়ার জন্য নিচের কমান্ড দিতে হবে। এখানে প্রসেসর টাইপ, ক্যাশ, স্পীড, কোর এবং মেমরির (RAM) ও Swap মেমরির তথ্য পাওয়া যাবে। 
Step 02: Check CPU, RAM, and Disk Info:
-----------------------------------------------------------------
[root@hostX ~]# cat /proc/cpuinfo 
[root@hostX ~]# free -m
[root@hostX ~]# lsblk, df -HT (Available space in root (/) Partition) 
 ** Note: Host CPU 2 core, Free Memory 1 GiB, Free HDD - 10 GiB (Recommanded)
এখন প্যাকেজ বা RPM ইন্সটল করতে হবে, উপরের রেফারেন্স টেবিলে প্রধান RPM গুলার লিস্ট দেওয়া আছে। মুলত অনেকগুলা RPM
 ইন্সটল করতে হবে। তবে, আমরা যদি তিনটি (০৩) RPM ইন্সটল করি সাথে তাহলে প্রয়োজনীয় যত ডিপেন্ডেন্সি আছে সবকিছুই ইন্সটল হয়ে যাবে। 
Step 03: Package Install: 
---------------------------------------
[root@hostX ~]# yum install virt-manager* libvirt* qemu-kvm* -y
RPM ইন্সটল এবং চেক করা শেষ হলে, Virtualization সার্ভিসটি রিস্টার্ট দিতে হবে এবং সিস্টেম চালু হওয়ার সাথে সাথে  সার্ভিস যেন একটিভ (enable) হয় এজন্য সার্ভিসটি 'enable' করতে হবে। Virtualization সার্ভিসের নাম libvirtd.service নিচে কমান্ড দিয়ে দখানো হয়েছেঃ  
Step 04: Service Restart: 
---------------------------------------
[root@hostX ~]# systemctl restart libvirtd.service  
[root@hostX ~]# systemctl enable libvirtd.service 
আমাদের ভার্চুয়াল এনভায়রনমেন্ট রেডি এখন নতুন VM মেশিন (Guest Machine) তৈরি করা হবে। VM মেশিন তৈরি করা হবে GUI
ইন্টারফেস Virtual Machine Manager (VMM) এর মাধ্যমে। প্যাকেজ ইন্সটল করার পরে সিস্টেমে 'Application' মেনুতে
Virtual Machine Manager (VMM) চলে আসবে। নিচের পাথ অনুযায়ী গেলে পাওয়া যাবে। 
Step 05: Run Virtual Machine Manager:
----------------------------------------------------------------
Application => System Tools => Virtual Machine Manager (VMM)
