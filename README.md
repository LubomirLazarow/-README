2.Инсталиране на виртуална машина за програмиране

2.1.Виртуална машина Dalvik
Тъй като хардуерните възможности на джаджите, особено в началото на разпространението на мобилни устройства в сравнение с настолните компютри, са по-ограничени, Google изисква основно да пресъздаде Java Virtual Machine (JVM) като виртуална машина на Dalvik.
Dalvik VM приема генерирани файлове от класове на Java и ги обединява в един или повече Dalvik Executable (.dex) файлове. Основното предназначение на виртуалната машина Dalvik е да оптимизира изпълнението на Java код за свободно място и за зареждане на батерията. Затова, за разлика от настолните компютрите, окончателните изпълними файлове за операционната система Android няма да се състоят от стандартния байткод за JVM, а специални файлове с разширение .dex
В резултат на това, когато потребителят кликне върху иконата на приложението, Dalvik генерира машинен код от байткода на приложението, т.е. компилация на ЛТ. След това Android създава процес, който разпределя паметта и получава ресурсите на процесора, необходими за стартиране на програмата.
Поради използването на Dalvik на крайните устройства, не е необходимо да създаваме копие на приложението за всяко отделно устройство, тъй като самият Dalvik оптимизира приложението за дадена платформа.

2.2.Виртуална машина Android RunTime
Започвайки с Android 4.4. KitKat в Android OS беше добавена втора виртуална машина - Android RunTime. Въпреки че в същата версия на Android 4.4 по подразбиране е Dalvik предпочитаната среда за изпълнение на кода на приложението, но вече в Android 5.0 версия Lollipop виртуалната машина Android RunTime напълно замени Dalvik.
Android RunTime се различава фундаментално от Dalvik: Android RunTime използва предварително компилиране на приложението, когато е инсталирано на мобилно устройство, а не компилация на ЛТ, което увеличава производителността на приложението.
2.3.Инсталиране на инструменти за разработка

Java
На първо място, за да създадем приложение, трябва да изтеглим и инсталираме пакета JDK 8, който е необходим за развитието на езика Java. JDK 8 може да се намери на уебсайта на Oracle: https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html 

Инсталиране на Android Studio
Има различни среди за разработка за Android. Могат да се използват среди като NetBeans, Eclipse или Visual Studio за разработка. Препоръчителната среда за разработка е Android Studio.

Настройка на Android SDK
Всичко, което правим на Android с помощта на Java, зависи от комплекта за разработване на софтуер за Android от Android SDK - ако създадем приложение за конкретна версия, например за Android Nougat, тогава трябва да имаме инсталирани съответните инструменти за SDK. Това трябва да се вземе предвид при разработването.
Отворяме Android Studio. По подразбиране, ако стартираме програмата за първи път, ще получим стартово меню. В дъното на стартовия екран на програмата намираме бутона - "Configure" - "Конфигуриране" и кликваме върху него. След това в падащото меню кликваме върху "SDK Manager". След което ще се отвори прозорецът с настройките за Android SDK Manager.

3. Създаване на приложение 

Сега ще създадем едно елементарно базово приложение в средата на Android Studio за операционната система Android. Отворяме Android Studio и в началния екран избираме - Start new Android Project: "Стартиране на нов проект за Android:
 

След това ще се покаже диалоговият прозорец за създаване на нов проект:
 
В следващата стъпка избираме шаблона на проекта. Android Studio предоставя редица шаблони за различни ситуации, но най-често срещаните са Basic Activity и Empty \ Activity. Това са най-удобните шаблони за започване на създаване на повечето приложения. В този случай ще изберем шаблона Empty Activity.
В следващият прозорец за създаване на нов проект можем да зададем първоначалните настройки:
- В полето Application Name въвеждаме името на приложението. Да наречем името HelloApplication.
- В полето Company Domain - Фирмен домейн, посочваме домейна на приложението или пакета клас, където ще се намира основният клас приложения. Също така е най-добре незабавно да присвоим определена стойност в полето Company. Domain - Домейн на компанията. Факт е, че когато хостваме приложение в магазина на Google Play, стойността за това поле трябва да е уникална за целия магазин. Въпреки че за тестови проекти, както в този случай, можете да оставим стойността по подразбиране в това поле.
- В полето Project Location - Местоположение на проекта можем да зададем местоположението на файловете на проекта на твърдия диск.
След това кликваме върху бутон
а Next - Напред и преминаваме към следващата стъпка. Ha тази стъпка ще бъдем помолени да зададем минималната поддържана версия на проекта. Версията по подразбиране е Android 4.1.1, която обхваща повече от 95% от устройствата с Android. Оставяме го по подразбиране и кликваме върху бутона Next - Напред.
При избора на следващата стъпка, трябва да зададем няколко настройки за проекта:
■	Activity Name: наименование на главния клас на приложението;
■	Layout Name: наименование на файла xml, в който ще се запази дефиницията на визуалния интерфейс;
■	Generate Layout File: необходимо ли е да се генерира файл xml с определение на визуалния интерфейс;
■	Backwards Compatibility (AppCompat): в маркирано състояние ви позволява да установите обратна връзка между различните версии на Android.

3.1. Структура на проекта
След като проектът бъде създаден, структурата на проекта на Android се показва в следната форма:
 

Проектът за Android може да се състои от различни модули. По подразбиране, когато създаваме проект, създаваме един модул -арр, приложение.
Модулът има три подпалки:
- manifests: съхранява манифестния файл AndroidManifest.xml, който дефинира конфигурацията;
- java: съхранява файлове на код на език java, които са структурирани по отделни пакети;
- res: съдържа използваните в приложението ресурси.
Отделният елемент Gradle Scripts съдържа няколко скрипта gradle (за модула на приложението, за други възможни модули и за целия проект), които се използват за изграждането на приложението.
Нека да преминем към пълната структура на проекта. За целта кликваме два пъти върху името на проекта. След това проектът ще се отвори напълно.
Ще разгледаме пълната структура на проекта за приложение под Android OS, която е създадена по подразбиране. Тук ще видим и единствения модул на проекта - модула на приложението. Всъщност целият код, с който ще работим, се намира вътре в този модул.
Всички модули в проекта се описват във файла за настройка setting.gradle. По подразбиране той има следното съдържание:

include ':арр'

Файлът build.gradle съдържа информацията, която се използва за изграждането на проекта.
Всеки модул има свой файл build.gradle, който определя конфигурацията на построения проект, специфична за дадения модул. Така че, ако погледнем съдържанието в папките на приложението, ще намерим такъв файл. В началния етап тези файлове не са толкова важни, достатъчно е само да разберем за какво са.
В модула на приложението - арр може да видите няколко папки и файлове, от които най-важните за нас са:
• каталог libs - е предназначен за съхранение на библиотеки, използвани от приложението;
• каталог src - е предназначен за съхраняване на изходния код. Той съдържа няколко поддиректории. Каталозите androidTest и test са предназначени за съхраняване на тестови файлове за приложенията. А действителният изходен код се намира в главната папка main.
• AndroidManifest.xml представлява манифесния файл, който описва основните характеристики на приложението, неговата конфигурация определя всеки от компонентите на това приложение.
• Папката java съдържа изходните файлове за приложението. По подразбиране тя съдържа файла на класа MainActivity, който се стартира по подразбиране при стартиране на приложението.
• Папката res съдържа директории с ресурси, по- специално съдържа следните директории:
-	папка drawable предназначена за съхраняване на изображения, използвани в приложението;
-	папка layout е предназначена за съхраняване на файлове, които определят графичен интерфейс. По подразбиране има файл activitymain.xml, който определя интерфейса за единствената в проекта activity - MainActivity;
-	папка mipmap-xxxx съдържа файлове с изображения, прикрепени за създаване на икона на приложението при различни резолюции на екрана;
-	Съответно за всяа разделителна способност на екрана има свой каталог;
-	папка values съхранява различни xml-файлове, съдържащи колекции ресурси - различни данни, които се използват в приложението.

3.2. Първо приложение
Стандартният проект вече съдържа известна функционалност. Вярно е, че това функционално прави почти нищо, извежда само на екрана поздрава "Hello world!".
В студиото файлът activity main.xml трябва да бъде отворен по подразбиране. Той съдържа дефиницията на графичния интерфейс на приложението.
Ако файлът се отвори в дизайна на дизайнера и дизайнът на приложението се показва в центъра на Android Studio, трябва да превключим изгледа на файла към текста.
За да се превключи режима - от текст към графика и обратно, има два бутона: дизайнерски - Design и текстови Text.
Сега ще променим кода на приложението, така че да се показва на екрана текста "Hello Android". За да направим това, променяме кода във файла activitymain.xml, който сега изглежда по следния начин:


 

Да променим дефиницията на елемента TextView в този файл, който е отговорен за показването на текстова информация на екрана на мобилното устройство. Самият изходен текст се определя с атрибута android:text. Следователно променяме целия код във файла activity main.xml, както следва:

<?xml version="l. 0" encoding="utf-8"?>
<RelativeLayout
xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:tools="http://schemas.android.com/tools"
android:id="@+id/activity_main"
android:layout_width="match_parent"
android:layout_height="match_parent"
android:padding="16dp">
CTextView
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:text="Hello Android!" />
</RelativeLayout>


След като запазим файла, можем да преминем към графичния изглед и да видим, че графичният дизайнер автоматично ще обновява и извежда вече дефинирания низ, който сме променили.

3.3. Клас Activity и ресурси	
Activity се явява клас, който по същество представлява отделен екран на приложението (страница) или неговия визуален интерфейс. Отделните activity, които вече се използват непосредствено в приложението, се явяват наследници от този клас. Приложението може да има едно activity, а може и няколко. Всяко отделно activity задава отделен прозорец за показване.
Ще разгледаме кода Activity, който се генерира автоматично в Android Studio (кодовият файл може да бъде намерен в проекта в папката src/main/java).
Класът MainActivity представлява обичаен клас Java, в началото на който има дефинициите на пакета и импортирането на външни пакети. По подразбиране той съдържа само един метод onCreate (), в който всъщност е създаден целият интерфейс на приложение.
В метода OnCreate() идва обръщение към метода на родителския клас и установяване на ресурса на дизайна:

super.onCreate(savedlnstanceState); setContentView(R.layout.activity_main);

За да зададем ресурса за маркиране на проекта, се извиква методът setContentView, на който е предаден идентификаторът на ресурса.
Нека обърнем внимание как изглежда идентификаторът на ресурса: R.layout.activity main. Всъщност това е връзката към файла activity_main.xml, който се намира в директорията res/layoat:

<?xml version="l.0" encoding="utf-8"?>
<RelativeLayout
xmlns:android="http://schemas.android.com/apk/res/and roid"
xmlns:tools="http://schemas.android.com/tools*'
android:id="@+id/activity_main"
android:layout_width="match_parent"
android:layout_height="match_parent"
android:padding="16dp">

<TextView
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:text="Hello Android!" />
</RelativeLayout>

Целият интерфейс е представен от контейнерен - елемент RelativeLayout, който съдържа един компонент - текстовото поле TextView. Текстовото поле определя текста, като използва атрибута android:text.

<TextView
android:layout_width="wrap_content" 
android:layout_height="wrap_content" 
android:text="Hello Android!"/>

По този начин, когато се стартира приложението, първо се стартира класът MainActivity, който в качеството на графичен интерфейс установява маркера от файла activity_main.xml като GUI.
Въпреки това, в класа MainActivity не използваме файловете, а идентификаторите на ресурси: R.layout.activity_main.
Всички идентификатори на ресурсите се определят в клас R, който автоматично се създава от помощната програма appt и се намира в файла R.java в директорията: build/ generated/source/r/debug:
Класът R съдържа идентификатори за всички ресурси, които се намират в директорията res. За всеки тип ресурс от клас R се създава вътрешен клас (например, за всички графични ресурси от директорията res/drawable се създава клас R.drawable) и за всеки ресурс от този тип се определя идентификатор. С този идентификатор можем впоследствие да извлечем ресурса в кодовия файл.
Когато актуализираме ресурсите при компилиране, този файл също се актуализира.
Например по подразбиране има ресурс за маркиране на интерфейс activitymain.xml, който се предава чрез идентификатора R.layout.activity_main. Но ако добавим нов ресурс за маркиране към папката res/layout, например mylayout.xml, тогава класа R се прекомпилира автоматично и можем да използваме незабавно този ресурс: setContentView (R.layout.my_layout);

3.4. Създаване на графично приложение
Графичният потребителски интерфейс се основава на йерархията на обектите View и ViewGroup. Обектите View представляват уиджети, като бутони или текстови полета. Обектите ViewGroup са контейнери за уиджети, контролират тяхното разположение и оформление.
Така че нека да създадем нов проект за приложения по начина, който използвахме по-рано. Или да използваме предишния проект. 

Създаване на линеен маркер
Избраният при създаването на activity шаблон EmptyActivity добавя цялата дефиниция на GUI към файла activity main.xml, който се намира в проекта в папката res/layout, така че ще променим файла activity main.xml както следва:

<?xml version»"1.0" encoding=”utf-8"?>
<LinearLayout
xmlns: android="http://schemas.android.ccm/apk/res/android“
android:layout_width="match_parent"
android: layout_height="match_parent"
android:orientation="horizontal" >
</LinearLayout>

Тук е дефиниран елементът LinearLayout, който се явява подклас на ViewGroup, в който са разположени дъщерните елементи в хоризонталния или вертикалния ред. Ориентацията на елементите се посочват в атрибута android:orientation. Всеки елемент в контейнера LinearLayout се показва на екрана в реда, в който е деклариран в XML файла.
Другите два атрибута - android:layout_width и android:layout_height са задължителни за всички приспособления за определяне на размерите. Тъй като LinearLayout е коренният елемент на оформлението, той трябва да запълни цялото пространство на екрана, така че стойността "matchjparent" е зададена за неговата височина и ширина. Тази стойност удължава приспособлението до границите на родителския контейнер.
3.5. Добавяне на текстово поле
За да добавите текстово поле вътре в елемента LinearLayout, създайте елемента EditText. Както всеки обект View, за EditText също трябва да декларирате определени xml- атрибути:

<EditText android:id="@+id/edit_message"
android:layout_width="wrap_content" 
android: layout_height="wrap_content"
android:layout_weight="1"
android:hint="Въведете съобщение" />

Така че, ние сме определили следните атрибути:
■	android:id: предоставя уникален идентификатор на уиджета - приспособлението, чрез който можем да се позовем на обекта;
■	Знак (@) за посочване на- справочен обект в XML файл. След това идва тип ресурс (в този случай id), наклонена черта и след това името на ресурса (edit_message);
■	Знакът "плюс" (+) пред типа на ресурса е необходим, когато ID на ресурса се определя за първи път. Когато компилирате приложение, комплектът за разработване на софтуер (SDK) използва името на идентификатора, за да създаде нов ID ресурс във файла gen/R.java. След това вече не трябва да използвате знака "плюс".
■	android:layout_width и android:layout_height: за тези свойства задайте стойност на wrap_content, която ще настрои за уиджетите величини, достатъчни за показване в контейнера;
■	android:layout_weight: ви позволява да определите ширината, заемана от полето. Стойността 1 в този случай ви позволява да разпънете полето до пълната ширина.android:hint: Задава текста, който ще се показва в текстовото поле по подразбиране, когато е празен.


3.6. Добавяне на бутони
Сега добавяме бутона „Button“ във файла activity_main.xml - елемент Button непосредствено след елемента EditText:
<Button
android:layout—width="wrap_content" 
andfoid:layout—height="wrap_content" android:text="Изпращане" />

В случай на бутон, неговата височина и ширина също имат стойност wrap_content, така че бутонът ще има такива размери, които са достатъчни за показване на текста върху него. За бутона не е необходимо да посочим атрибута android:id, тъй като няма да се отнасяме към него в кода MainActivity
В резултат на това файлът ще изглежда така:

<?xml version="l.0" encoding="utf-8"?>
<LinearLayout
xmlns:android="http://schemas.android.com/apk/res/andro id"
android:layout—width="match_parent"
android:layout—height="match_parent"
android:orientation="horizontal" >
<EditText android:id="@+id/edit_message"
android:layout—width="wrap_content"
android:layout_height="wrap_content"
android:layout—weight="1"
android:hint="Въведете съобщение" />
<Button
android:layout_width="wrap_content" 
android:layout_height="wrap_content" 
android:text="Изпращане" /> .
</LinearLay out>

И в момента приложението ще има следния интерфейс:

 

3.7. Стартиране на второ ACTIVITY
За да свържем манипулатора на бутони, отваряме файла activity_main.xml и добавяме в елемента Button атрибута android :onClick:

<?xml version-'1.0" encoding="utf-8"?>
<LinearLayout
xmlns:android="http://schemas.android.com/apk/res/android" android:layout_width="match_parent" 
android:Iayout_height="match_parent" 
android:orientation="horizontal" >
<EditText android: id="@+id/edit_message" 
android:layout width-'wrapcontent" 
android:layout_height-'wrapcontent" 
android:layout_weight="l" 
android:hint="Въведете съобщение" />
<Button 
android:layout_width-'wrap_content" 
android:layout_height="wrap_content" 
android:onClick="sendMessage" android:text="Изпращане" />
</LinearLayout>

Стойността "sendMessage", присвоена на атрибута android:onClick, представлява по себе си името на метода, определен в класа activity, който системата извиква, когато потребителят кликне върху бутона. Сега ще определим този метод.

Създаване на обект Intent
Отиваме при класа MainActivity, който се намира в проекта в папката app/src/main/java/package_name и променяме този клас както следва:
package com.example.*****.helloapplication;
import android.content.Intent; // включваме класа Intent
import android.support. v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View; // включваме класа View за обработка при натискане на бутони
import android.widget.EditText; // включваме класа EditText
public class MainActivity extends AppCompatActivity {
public final static String EXTRA_MESSAGE = "EXTRA_MESSAGE" ;
@Override
protected void onCreate(Bundle savedlnstanceState) { 
super.onCreate(savedlnstanceState) ; 
setcontentview(R.layout.activity_main);
)
// Метод за обработка натискането на бутоните public void sendMessage(View view) {
// действия, извършващи се след натискането на бутона
// Създаваме обект Intent за извикване на ново Activity Intent intent = new Intent (this,DisplayMessageActivity.class) ;
// Получаваме текстово поле в текущия Activity
EditText editText = (EditText)
findViewByld(R.id.edit_message) ;
// Получаваме текст в текстовото поле
String message = editText.getText().toString();
// Добавяме c помощта на свойствата putExtra обект - първи параметър - ключ,
// втори параметър - значение на този обект intent.putExtra(EXTRA_MESSAGE, message);
// стартиране на activity startActivity(intent);
}
}
Тук току-що е добавен методът sendMessage(), който ще бъде извикан чрез натискане на бутона. Обработчикът за кликване върху бутоните трябва да приеме обекта "View" като параметър, който представлява самото натискане на бутон:

public void sendMessage(View view) {

След това, за да изпълните второ activity, имате нужда от обект Intent. Обектът Intent представлява задача за приложение, която трябва да бъде изпълнена (например стартиране на activity):

Intent intent = new Intent(this, DisplayMessageActivity.class);

Конструкторът на този обект има два параметъра:
■	Първият параметър представлява контекстния обект Context (ключовата дума this се използва тук, тъй като класа MainActivity се явява подклас на класа Context);
■	Вторият параметър е класа на компонента, на който ние предаваме обекта Intent. На него ще действа обектът DisplayMessageActivity, който ще създадем след малко.
Вътре в метода sendMessage(), използваме метода findViewByld, за да получим елемента EditText и да предадем стойността на неговия текст в обекта intent:

EditText editText = (EditText) findViewByld(R.id.edit_message);
String message = editText.getText().toString();

След това текста, получен от текстовото поле, се прехвърля на стартиращия се activity.

intent.putExtra(EXTRA_MESSAGE, message);

Параметърът "EXTRAMESSAGE" показва ключа на предаваните данни. Това означава, че можем да прехвърлим много данни в новото activity и за да можем да ги различим между тях, е определен ключ.
В този случай ключът EXTRAJVIESSAGE е обичаен низ "EXTRA MESSAGE":

public final static String EXTRA_MESSAGE = "EXTRA_ME5SAGE";
За стартиране на activity, трябва да извикате метода startActivity () и да предадете на него в качество на параметър обекта Intent:

startActivitу(intent);

След извикване на този метод, системата ще получи сигнал и ще стартира нов обект Activity, определен от обекта Intent.

Създаване на втори обект Activity
Сега добавяме ново activity - DisplayMessageActivity. За да направим това, щракваме с десния бутон на мишката върху структурата на проекта в папката на пакета, където се намира класа MainActivity, а в контекстното меню избира

 

И след това кликваме върху Finish.
Така ние създадохме ново activity: нов клас DisplayMessageActivity се добавя към папката app/src/main/java/[име_нa_пакети], а activity display message.xml с дефиницията на новата дейност се добавя към app/src/main/res/layout.
Отворяме класа DisplayMessageActivity и го променяме, както следва:

package com.example.****.helloapplication;
import android.content.Intent;
import android.support. v7.app.AppCompatActivity;
import android.os.Bundle;
import android.widget.Textview;
public class DisplayMessageActivity extends AppCompatActivity {
@Override
protected void onCreate(Bundle savedlnstanceSta te) 
{
super.onCreate(savedlnstanceState);
// Получаваме съобщение от обекта intent
Intent intent = getlntentO;
String message =
intent.getStringExtra(MainActivity.EXTRA_MESSAGE);
// Създаваме текстово поле
Textview textview = new Textview(this); textView.setTextSize(40);
textview.setText(message);
// Устанавяваме текстовото поле в системата, на компоновки activity
setContentView(textview);
}
}

В MainActivity (и в други activity), създаването на текущия activity се извършва по метода onCreate(). Всички подкласове на Activity трябва да прилагат метода onCreate, тъй като системата го извиква, когато създава ново activity. В този метод оформлението на обекта за ново activity е зададено чрез метода setContentView и тук, произтича първоначалната конфигурация на компонентите.

Показване на съобщение на екрана
В началото ние предавахме от нашото първо и главно activity в DisplayMessageActivity текстово съобщение, въведено в текстовото поле. Сега ще го получим в DisplayMessageActivity и ще го изведем на екрана.
Всеки обект на Activity се извиква от обекта на Intent. Можем да получим извикващия обект Intent с помощта на метода getlntent и по този начин да получим данните, изпратени от него.

Intent intent = getlntent();
String message = intent.getStringSxtra(MainActivity.EXTRA_MESSASE);

За да покажете съобщението на екрана, създайте уиджет TextView и задайте текста с помощта на свойството setText. След това добавете нов уиджет в DisplayMessageActivity, като използвате метода setContentView.

TextView textView = new TextView(this); textView.setTextSize(40);
textView.setText(message); setContentView(textView);

След като стартираме приложението на емулатора, отново ще видим текстовото поле с бутона, но след въвеждане на текст и щракване върху бутона ще се стартира нов activity и ще се появи друг екран със съобщението, въведено по-рано в текстовото поле.
