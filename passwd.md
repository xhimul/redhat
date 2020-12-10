আজকে আমরা শিখব লিনাক্স এর পাসওয়ার্ড রিলেটেড কিছু কমান্ড যে কমান্ড গুলো কোনো ইউজার এর পাসওয়ার্ড set/reset/remove করতে লাগে।
.
➡01. প্রথমে Root ইউজার এর পাসওয়ার্ড সেট বা রিসেট করতে নিচের কমান্ড:
[root@serverX ~]# passwd 
New Password: ****** 
Retype New Password: ******
.
➡02. Root ইউজার কতৃক অন্য রেগুলার ইউজার এর পাসওয়ার্ড ইউজার এর পাসওয়ার্ড সেট বা রিসেট করতে নিচের কমান্ড:
[root@serverX ~]# passwd [user name]
[root@serverX ~]# passwd student
New Password: ****** 
Retype New Password: ******
.
➡03. যেকোনো ইউজার এর পাসওয়ার্ড রিলেটেড ইনফরমেশন (যেমন, পাসওয়ার্ড দেওয়া আছে কিনা, সর্বশেষ পাসওয়ার্ড পরিবর্তন তারিখ, সর্বোচ্চ/সর্বনিন্ম পাসওয়ার্ড মেয়াদ এবং পাসওয়ার্ড এর এনক্রিপশন (SHA/MD5) মেথড) জানতে চাইলে নিচের কমান্ড:
[root@serverX ~]# passwd -S [user name]
[root@serverX ~]# passwd -S root
[root@serverX ~]# passwd -s student
.
➡04. কোনো ইউজার এর পাসওয়ার্ড ডিলিট অথবা পাসওয়ার্ড ছাড়া লগইন পারমিট দিতে চাইলে নিচের কমান্ড:
[root@serverX ~]# passwd -d [user name]
[root@serverX ~]# passwd -d student 
[root@serverX ~]# passwd -d root 
.
➡05. কোনো ইউজার এর পাসওয়ার্ড পরিবর্তন করাতে বাধ্য করার জন্য নিচের কমান্ড:
[root@serverX ~]# passwd -e [user name]
[root@serverX ~]# passwd -e student 
.
➡06. কোনো ইউজার এর পাসওয়ার্ড লক (lock) করতে চাইলে নিচের কমান্ড:
[root@serverX ~]# passwd -l [user name]
[root@serverX ~]# passwd -l student
.
➡07. কোনো ইউজার এর পাসওয়ার্ড একটিভ আনলক (un-lock) করতে চাইলে নিচের কমান্ড:
[root@serverX ~]# passwd -u [user name]
[root@serverX ~]# passwd -u student
➡08. কোনো ইউজার এর পাসওয়ার্ড এর সর্বনিন্ম মেয়াদ সেট করতে চাইলে নিচের কমান্ড:
[root@serverX ~]# passwd -n 3 [user name]
[root@serverX ~]# passwd -n 3 student
নোট: অর্থাৎ স্টুডেন্ট ইউজার তিন দিনের আগে তার পাসওয়ার্ড পরিবর্তন করতে পারবে না।
.
➡09. কোনো ইউজার এর পাসওয়ার্ড এর সর্বোচ্চ মেয়াদ সেট করতে চাইলে নিচের কমান্ড:
[root@serverX ~]# passwd -x 30 [user name]
[root@serverX ~]# passwd -x 30 student 
.
নোট: অর্থাৎ স্টুডেন্ট ইউজার তার বর্তমান পাসওয়ার্ড টি সর্বোচ্চ ৩০ দিন ব্যবহার করতে পারবে।
