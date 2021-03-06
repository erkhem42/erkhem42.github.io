---
layout: post
title:  "Docker гэж юу вэ ? Хэн юунд ашигладаг, яагаад нийтээрээ ингэж давалгаалаад байгаагын учир"
date:   2015-03-25 17:42:33 +0800
categories: docker
---

## Docker гэж юу вэ ? 

Докер бол тархсан (distributed) програм хөгжүүлэх, тестлэх, серверт байрлуулах (deployment) зэрэг бүхий л ажилуудаа контэйнер-ыг (доор дэлгэрэнгүй тайлбарласан болно) ашиглан хялбарчилж, виртуал машины дараах үе болж гарч ирсэн шинэ технологи юм.
Докер нь нээлттэй эх дээр суурьтай хөгжүүлэгддэг бөгөөд програмыг өөр хоорондоо уялдаа холбоо багатай компонентуудаас (модуль, програмын нэгэн дэд хэсэг) бүрдүүлж ажилуулах боломж олгохоос гадна хөгжүүлэх, тэстлэх болон сервер хоорондын орчнуудын ялгааг арилгадаг.
Илүүг [эндээс](https://docs.docker.com/introduction/understanding-docker/) үзнэ үү.

### Docker container:

Докер контэйнер нь программыг шаардлагатай бүхий л хэсгүүдтэй цуг хайрцагласан, тээвэрлэхэд зориулагдсан package сав гэж ойлгож болно. Ингэснээр таны програм хөгжүүлсэн компьютерийн тань үйлдлийн системээс үл хамааран, хаана ч зөөж, ажиллуулахад боломжтой болно.
Контэйнэр-ыг docker image-с үүсгэдэг. Энэ image нь ubuntu, debain гэх зэрэг линуксын тархалтуудын аль нэг байж болно. Docker image талаар илүү дэлгэрэнгүйг [эндээс](https://docs.docker.com/introduction/understanding-docker/) мөн [эндээс](https://docs.docker.com/userguide/dockerimages/) үзнэ үү.

Энэхүү ойлголт нь уламжлалт програм - үйлдлийн системээс нягт хамааралтай байсан ойлголтыг өөрчилж програмыг илүү бие даасан, шаарлагатай тохиолдолд угсрагдах боломжтой байдлаар зохион байгуулагдахаар шийдэж чадсан юм. Жишээ нь: 
За та дэлхий хэмжээний нэгэн технологийн компанид хөгжүүлэгчээр ажилладаг гэж үзье.
Танай ажилладаг төсөл дээр олон улсаас олон тооны хөгжүүлэгчид зэрэг ажилладаг бөгөөд өдөр бүр шинэ шинэчлэлтийг сервертээ хийдэг гэж бодъё. Тэгэхээр хөгжүүлэгч таны компьютер дээр байгаа программуудын хувилбар, ашигладаг сангууд болон тохиргоонууд тань сервер дээрхтэйгээ яг таг таарч тохирхоос гадна ямар нэгэн зөрчилгүй байжийж та илүү баталгаатай, итгэлтэйгээр програмаа сервертээ байршуулнаа даа. Мэдээж хийхээсээ өмнө тестийн үе шатаар дамжих нь тодорхой.
Тиймээс яаж энэхүү бүх шат дараалалд  өөрийн програмаа хөгжүүлдэг компьютерийн үйлдлийн системээс болон бусад хамааралтай сангуудын хувилбараас үл хамааран ажиллах орчиноо ижилхэн байлгаж, мөн серверт байршуулж, шинэчлэх ажлыг илүү амар болгох вэ? Хариулт нь docker.

### Docker vs Virtual Machine

![Docker vs VM](/assets/image1.png)

Докер нь виртуал машин шиг бүх бүтэн үйлдлийн системийг виртуалиар үүсэхгүйгээр харин өөрийн тань ашиглаж буй тухайн Линукс үйлдлийн системийн Кэрнелыг ашигладаг ба зөвхөн шаардлагатай контэйнеруудыг ажилуулдагаараа виртуал машинаас илүү хурдан, мөн маш бага зайг эзэлдэг давуу талуудтай. Илүүг [эндээс](https://docs.docker.com/), [эндээс](http://stackoverflow.com/questions/16047306/how-is-docker-io-different-from-a-normal-virtual-machine) мөн [эндээс](http://opensource.com/resources/what-docker).

## 2. Хэн юунд ашигладаг, яагаад нийтээрээ ингэж давалгаалаад байгаагын учир

Докер бол хөгжүүлэгчид яг сервертэй ижил орчинд ажиллах боломжыг, систем админуудад тус тусдаа нэг нэг хайрцаганд (контэйнэрт)  багтах програмуудыг үүсгэж, холбож, сервер хооронд хялбархан зөөж, удидах боломжуудыг олгодог.

**Маш хялбархан жишээ авъя:** 

Та нэг блогын сайт ажилуулдаг гэж бодъё. Тэгэхээр таньд веб сервер (Nginx, Apache) , өгөгдлийн бааз (Mysql, Postgresql, MongoDB, .. гм), аль нэг хэлний [CMS](http://en.wikipedia.org/wiki/Content_management_system) (Wordpress, Drupal, Joomla) эсвэл [фраймворк](http://en.wikipedia.org/wiki/Web_application_framework) (Django, ruby on rails, symfony …гт) гэх мэт хэрэг болно. Тэгэхээр энгийнээр та `nginx` сервер, `mysql`  өгөгдлийн бааз болон `wordpress` CMS ашигладаг гэж үзье.
Тэгэхээр докерыг энэхүү блогын апп-даа яаж ашиглах вэ гэхлээр:
Та өгөгдлийн баазаа тусд нь нэг контэйнэрт, блогын системээ хөгжүүлэх `wordpress` кодоо (эх кодоо контэйнэртоо mount хийж оруулна) болон серверүүдээ өөр нэгэн контэйнэрт хуваагаад, хооронд нь холбож ажиллахаар тохируулна. Ингэж өгөгдлийн бааз болон бусад 3 дагч байдлаар шаардагдах сангуудыг тусгаарласнаар (isolation), програмаа серверт байршуулах, өөр бусад сервисүүдтэй холбох, олон хувилбаруудтэй нэгэн зэрэг (хувилбар бүрийг өөр өөр контэйнэрт) ажиллах зэрэгт илүү хялбар, нээлтэй болж байгаа юм.


### Хийгдэх алхамууд:

1. docker -г өөрийн ашигладаг үйлдлийн систем дээрээ суулгана. Зааврыг [эндээс](http://docs.docker.com/installation/#installation) харна уу
2. `docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=mysecretpassword -d mysql` команд ашиглаж mysql баазын image-ыг татаж, контэйнерыг ажиллуулна. Илүүг [эндээс](https://registry.hub.docker.com/_/mysql/) харна уу
3. `docker run --name some-wordpress --link some-mysql:mysql -d wordpress` командыг ашиглан wordpress -ыг мөн контэйнер татаж суулгаж, ажиллуулна. `--link` гэсэн сонгот нь 2 дахь алхам дээр үүсгэсэн mysql -ын some-mysql гэсэн нэрээр үүссэн контэйнертээ холбож өгч байна. Илүүг эндээс.

Таны бааз болон бусад сангууд тус тусдаа нэг контэйнэрт ажилладаг болсноор, та өөрийн үндсэн үйлдлийн систем дээрээ зөвхөн програмын эх кодоо хадгалахад хангалттай болох юм. Ингэснээр  та өгөгдлийн бааз болон бусад хамааралтай програмын хувилбар өөрчлөх шаардлага гарвал өмнөх байгаа хувилбараа устгахгүйгээр дахин нэг контэйнэр үүсгээд, тэрэнтэйгээ холбоход л хангалттай юм.

Бие биенээсээ нягт хамаарахгүй, шаардлагатай бол холбогдох боломжтой болгон хайрцаглаж контэйнэрт хийснээр програм хөгжүүлэх, ажиллуулж, тестлэх болон серверүүдэд нүүлгэхэд илүү хялбар болж байгаа юм.

## 3. Яагаад ibm, google, microsoft, amazon, ebay, Yandex ... гэх технологийн аваргууд докерыг дэмжиж, ашиглаад байна ?

Технологийн том компаниуд өөрсдийн хэдэн мянган серверүүддээ докер-г ашигласнаар дискний зайгаа илүү үр бүтээлтэй хувиарлаж ашиглахаас гадна, процесуудыг хянаж удирдаж, тохируулахад илүү боломжийг олгодог учираас ийнхүү давалгаалж байгаа юм.  
Илүү дэлгэрэнгүйг мэдэхийг хүсвэл доор хэдэн холбоосоор орж сонирхоорой.
1. [IBM and Docker Announce Strategic Partnership to Deliver Enterprise Applications in the Cloud and On Prem](https://www-03.ibm.com/press/us/en/pressrelease/45597.wss)
2. [Containers on Google Cloud Platform](https://cloud.google.com/compute/docs/containers)
3. [Technology & Service Providers](https://www.docker.com/partners/find/)


Энэхүү бичлэгээр хэрэв та докерын тухай сонирхсон боловч хэрхэн яаж ашиглахыг хараахан мэдэхгүй байгаа бол товч ойлголтыг өгөхийг зорьсон болно.
Оруулсан мэдээлэл ямар нэгэн алдаа, залруулга байвал сэтгэгдэл бичээрэй.

За амжилт!

