# DDS & ROS 2 Interoperation

1. Autonomous Vehicle Evolution
2. Modern Autonomous Vehicles
3. Dataflow Challenge
4. Evolution of Networking
5. 200+ RTI Autonomous Vehicle Programs!
6. Connectivity Framework
7. 15+ Standards and Consortia Efforts
8. Flying Cars
9. Enable UAS Flight in National Air Space
10. Handle Safety-Critical Systems
11. Resilience


### (preview) DDS architecture.

1. DDS Standard Family
> area ၃ ခုနဲ့အလုပ်လုပ်ပါတယ်။ အပေါ်ဆုံး DDS Software API ရှိမယ်။ အောက်မှာတော့ wire protocol တစ်ခုဖြစ်တဲ့ Realtime Publish, subscribe Wire Protocol (RTPS) ရှိပါတယ်။ plugin Security တစ်ခုပါပါမယ်။​
> DDS က Open Standard Family ဖြစ်ပါတယ်။ Open Source နဲ့ ကွာခြားချက်ကတော့ အများကြီးအားသာချက်ရှိပါတယ်။ ဥပမာ- Linux က Open Source ဖြစ်ပါတယ်။ကျွန်တော်တို့ကိုယ်ပိုင် Customized Linux OS လိုအပ်တဲ့အချိန်ကျရင်တော့ source code တွေကို ဆွဲယူပြီး ကိုယ်ပိုင် standared နဲ့သွားပြီးလုပ်ရမှာဖြစ်သလို ကိုယ်ပိုင် procedure တွေနဲ့ implement လုပ် integrate လုပ်ပြီးအသုံးပြုရမှာဖြစ်ပါတယ်။ DDS ကတော့ သူ့ရဲ့ implementation တွေကို download ဆွဲပြီးကိုယ်ပိုင် commercial support implementation အဖြစ်နဲ့တန်းသုံးရုံပါပဲ။ 
2. DDS Highlights
> Data Centric ဖြစ်တာတစ်ခုက သူ့မှာ အားသာချက်တစ်ခုပါပဲ။ developer တွေက data transmission အတွက် စိတ်ပူစရာမလိုတော့ပါဘူး။ hardware တွေရဲ့ pheripheral တွေကို စိတ်ပူစရာမလိုတော့ပါဘူး။ automated discovery စနစ်ပါဝင်တဲ့အတွက်လည်း DDS RTPS Layer ထဲမှာရှိတဲ့ topic, service, request reply စတာတွေအတွက်လည်း auto ရှာဖွေ ပိုပေးသွားပါမယ်။ 
3. DDS Quality of Service
> large data တွေပို့တဲ့အခါ DDS က smaller chunks တွေအဖြစ်နဲ့ data ကိုခွဲထုတ်လိုက်ပါတယ်။ ပြီးမှ asynchronously အဖြစ်နဲ့ publish ပြန်လုပ်ပေးတာပါ။ quality of service settings ထဲမှာတော့ ကျွန်တော်တို့ Built-in QOS Profile ကို configure ချပေးရမှာပါ။ 

` struct StationValue {
	unsigned long ID; 
	unsigned long long count; 
	float temperature;
	}`

4. Data Communication
> data communiction အတွက် data centric ဖြစ်သွားတဲ့ DDS အတွက် ကျွန်တော်တို့ စိတ်ပူစရာမလိုတဲ့အပိုင်းတွေကတော့ messages, address, routing, broker တွေပါ။  DDS က data centric middleware အနေနဲ့ အလုပ်လုပ်ပေးတာဖြစ်တဲ့အတွက် စိတ်ပူစရာမလိုတော့တာပါ။ 
5. Use a central Broker ?
> central broker အနေနဲ့ အလုပ်လုပ်တာလား ဆိုရင် မဟုတ်ပါဘူး။ central broker အနေနဲ့ အလုပ်လုပ်မယ်ဆိုရင် broker node down တာနဲ့ သူ့ကို လာချိတ်ထားတဲ့ ကျန်တဲ့ node တွေအကုန် failed ကုန်မှာဖြစ်ပါတယ်။ central broker server ကြီးက ပိုစျေးကြီးတဲ့ equipment ဖြစ်နေနိုင်သလို၊ the most failure prone ကြီးလည်းဖြစ်ပါမယ်။ အာ့အတွက် central broker ပုံစံနဲ့ အလုပ်မလုပ်ပါဘူး။ 
6. DDS Creates This .... 
> DDS က Virtualized Data Bus တွေနဲ့ ခွဲပြီးအလုပ်လုပ်ပါတယ်။ transport independent ပုံစံဖြစ်ပြီး data topics တွေနဲ့ အလုပ်လုပ်ကြတာဖြစ်ပါတယ်။ ကဲ automated discovery လည်းပါဝင်တဲ့အတွက် publish data နဲ့ လိုအပ်နေတဲ့ subscribe data တွေ topic တူညီနေရင် point to point connection အနေနဲ့ shared memory တွေကိုအသုံးပြုပြီး အလုပ်စလုပ်ပါတယ်။ automated discovery process တွေကို radio link နဲ့ serial pheripherial တွေ နဲ့ တွဲပြီးအလုပ်လုပ်နေတာဖြစ်တဲ့အတွက် ကျွနော်တို့ စိတ်ပူစရာက implementation လုပ်ချိန်မှာ data တွေကိုပဲ foucs လုပ်ရတော့မှာဖြစ်ပါတယ်။ ဥပမာ - relibale မဖြစ်တဲ့ UDP networking က multicast ရပါတယ်။ အာ့ udp data bus ကို အသုံးပြုပြီး one publisher နဲ့ many subscribers တို့ကိုလည်း ဖန်တီးလိုက်လို့ရပါတယ်။ အာ့လိုဆို။ 
> ဘာပဲဖြစ်ဖြစ်လေ ပြန်ကြည့်မယ်ဆိုရင် DDS က brocker based system လို့မပြောပေမယ့် brocker based systems က ideas တွေအများကြီးထည့်သွင်းထားပါတယ်။ 
> DDS ရဲ့ နှလုံးသားလေးကတော့ Domain Participant ပဲဖြစ်ပါတယ်။ သူ့ထဲမှာ publishers တွေ subscribers တွေနဲ့ data reader, data writer တွေအပြင် topic တွေ buffer တွေကို created လုပ်ပေးရမှာပါ။ domain စုစုပေါင်း ၁ to ၂၄၈ ခု တည်ဆောက်လို့ရမှာဖြစ်ပါတယ်။ အာ့ domain တစ်ခုမှာ domain participant တွေပါဝင်ပါတယ်။ မတူညီတဲ့ domain မှာရှိနေတဲ့ application တွေက အချင်းချင်းစကားပြောနိုင်မှာ data တွေပို့ပေးနိုင်မှာမဟုတ်ပါဘူး။ 
7. Reliable Data
> Data တွေကို reliable ဖြစ်အောင် DDS က heartbeat mechanism တစ်ခုကို အသုံးပြုပြီး data တွေကို တိကျစွာသယ်ယူပို့ဆောင်နေစဥ်အတွင်းမှာရော ရောက်ရှိချိန်မှာရော၊ တခြား အချိန်တွေမှာရော (ဥပမာ - liveliness ကိုလိုအပ်တဲ့အချိန်မှာ ) တာဝန်ယူပေးပါမယ်။
8. History and Durability 
> Reliablity က စိတ်ချရမှုရှိပေမယ့် ပို့ထားတဲ့ data တွေအတွက် buffer history တွေကို ပြန်ကြည့်နိုင်ခြင်းကလည်း durability တစ်ခုပဲမဟုတ်လား။ domain participant တွေရဲ့ profile ကို QOS Settings ထဲက Transient local ဆိုတဲ့ကောင်ကိုသုံးကာ durability အတွက် သွားရောက်ပြီး history size များကို ဘယ် publisher နဲ့ ဘယ် subcribers နဲ့ ဘယ် topics တွေအတွက်ကိုပေးမလဲဆိုတာ သွားရောက်ချိန်ညှိလို့ရသည်။ 
9. Topic Data Types
> Heartbeat machin က Data တွေကို reliable ဖြစ်အောင် လုပ်ပေးတာ ဖြစ်ပါတယ်။ သူ က Acknowledge လုပ်ပြီး sender ရဲ့ history buffer ထဲက နေ Data Bus မှာ loss ဖြစ်သွားတဲ့ data တွေကို ပြန်ယူပေးနိုင်ပါတယ်။ အာ့အတွက် ကြောင့် sample data chunck တစ်ခုပို့တိုင်းမှာ subscriber ရဲ့ domainparticipent (သိုမဟုတ်) DDS Client ထဲကို heartbeat တွေနဲ့အတူ data တွေပါ ဝင်လာနေမှာပဲဖြစ်ပါတယ်။ 
9.1 Topic Data Types
> data Type တွေကို သတ်မှတ်တဲ့အခါ C Style sturcture ကိုသုံးပြီး dataတွေကို ကြေညာပေးလို့ရသလို xml နဲ့ json နဲ့ရောပြီး mixed type အနေနဲ့ အသုံးပြုလို့လည်းရပါသေးတယ်။ တစ်ခုဆိုတစ်ခုပဲသုံးတာကောင်ပါတယ်။ xml က loosely type ဖြစ်တယ်ပြောတာပဲ။ 
10. Data Type Extensibility Final Type
> Data type တွေသတ်မှတ်အသုံးပြုတဲ့အခါ ကိုယ်ချင်တဲ့ data တွေကိုပဲ filter လုပ်ပြီး ယူလို့ရပါတယ်။ ဥပမာ- temperature data 80 degree ကို threadshold ဖြတ်ချပြီး 50 မှယူမယ်ဆိုတာမျိုးကို content filtered topic အဖြတ်သတ်မှတ်ပေးနိုင်ပါတယ်။
> Final Type - သူကတော့ Type Define လုပ်ကတည်းက striped လုပ်ထားတာပါ။ extensible type - ဒီ type လေးကတော့ data fields ထဲကို new data types ထပ်မံ extend လုပ်ပြီးသုံးလို့ရတာကို ထပ်ထည့်ပေးလို့ရပါတယ်။ 
11. Topic Attributes
12. Discovery Process
13. RTI Admin Console
14. Request-Reply
15. Correlation
16. Single-Request Multiple-Reply
17. Multiple Repliers

### ROS2 is DDS. (Suprised)

1. What is ROS? (Robot Operating System) • ROS is not an Operating System - it's a Framework for Robot Software

2. Original ROS Architecture
3. ROS2 is DDS
4. ROS 2 Interoperability: Data Model
5. "RViz2" 3D Visualizer
6. Connext Pro Launcher
7. Admin Console: Data Visualization (2)
8. Distributed Logger
9. RTI Connector
