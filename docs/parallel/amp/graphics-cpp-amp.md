---
title: Grafika (C++ AMP) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 190a98a4-5f7d-442e-866b-b374ca74c16f
caps.latest.revision: "27"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 601cf58a8238e34b1186e9d5d022a315342d4e6e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="graphics-c-amp"></a>Grafika (C++ AMP)
C++ AMP zawiera kilka interfejsów API w [Concurrency::graphics](../../parallel/amp/reference/concurrency-graphics-namespace.md) przestrzeni nazw, która umożliwia dostęp do pomocy technicznej tekstury na procesorach GPU. Niektóre typowe scenariusze są następujące:  
  
-   Można użyć [tekstury](../../parallel/amp/reference/texture-class.md) klasy jako kontener danych obliczania i wykorzystać *przestrzennych miejscowości* tekstury pamięci podręcznej i układy procesora GPU. Lokalizacja przestrzennego jest właściwości elementów danych są fizycznie zbliża się wzajemnie.  
  
-   Środowisko uruchomieniowe zapewnia wydajne współdziałanie z programów do cieniowania z systemem innym niż obliczeń. Pikseli, wierzchołków tworzenia mozaiki i programów do cieniowania powłoki są często używają lub utworzyć tekstury, korzystających z C++ AMP obliczenia.  
  
-   Graficzne interfejsy API w języku C++ AMP zapewniają alternatywnych metod dostępu do programu word podrzędna spakowana buforów. Tekstury, które mają formaty reprezentujące *tekseli* (elementy texture) który składają się z 8-bitową lub 16-bitowych wartości skalarne zezwala na dostęp do takich magazynu spakowane dane.  
  
## <a name="the-norm-and-unorm-types"></a>Norm — i unorm — typy  
 `norm` i `unorm` typy są typy skalarne, które ograniczyć zakres `float` wartości, jest to nazywane *ładunku*. Te typy mogą zostać jawnie utworzone na podstawie innych typów skalarnych. W rzutowanie, wartość jest najpierw rzutowane na `float` , a następnie zablokowane za pomocą odpowiednich regionie, który jest dozwolony przez normy [-1,0, 1.0] lub unorm — [0.0, 1.0]. Rzutowanie +/-nieskończoności zwraca +/-1. Rzutowanie NaN nie jest zdefiniowana. Norm — może zostać niejawnie utworzone na podstawie unorm — i nie ma bez utraty danych. Operator niejawnej konwersji do typu float jest zdefiniowany w tych typów. Operatorów binarnych są definiowane pomiędzy te typy i inne wbudowane typy skalarne, takie jak `float` i `int`: +, -, *, /, =,! =, >, \<, > =, < =. Złożone operatory przypisania są również obsługiwane: +=,-=, \*= / =. Jednoargumentowy operator negacji (-) jest zdefiniowany dla typów normy.  
  
## <a name="short-vector-library"></a>Biblioteka krótkich wektora  
 Krótki biblioteki wektor zawiera niektóre z funkcji [typu wektora](http://go.microsoft.com/fwlink/p/linkid=248500) który jest zdefiniowany w HLSL i zazwyczaj jest używane do definiowania tekseli. Wektor krótkie jest strukturą danych, który przechowuje wartości 1 do 4 tego samego typu. Obsługiwane typy to `double`, `float`, `int`, `norm`, `uint`, i `unorm`. W poniższej tabeli przedstawiono nazwy typu. Dla każdego typu, jest również odpowiedniego `typedef` które nie mają znaku podkreślenia w nazwie. Typy, które mają znaki podkreślenia są w [Namespace Concurrency::graphics](../../parallel/amp/reference/concurrency-graphics-namespace.md). Typy, które nie mają znaki podkreślenia są w [Namespace CONCURRENCY::Graphics:: Direct3D —](../../parallel/amp/reference/concurrency-graphics-direct3d-namespace.md) tak, aby ich wyraźnie rozdzieleniu z typów podstawowych podobnie o nazwie takich jak `__int8` i `__int16`.  
  
||Długość 2|Długość 3|Długość 4|  
|-|--------------|--------------|--------------|  
|double|double_2 —<br /><br /> double2|double_3 —<br /><br /> double3|double_4 —<br /><br /> double4|  
|float|float_2 —<br /><br /> float2|float_3 —<br /><br /> float3|float_4 —<br /><br /> FLOAT4|  
|int|int_2 —<br /><br /> int2|int_3 —<br /><br /> int3|int_4 —<br /><br /> int4|  
|norm|norm_2 —<br /><br /> norm2|norm_3 —<br /><br /> norm3|norm_4 —<br /><br /> norm4|  
|uint|uint_2 —<br /><br /> uint2|uint_3 —<br /><br /> uint3|uint_4 —<br /><br /> uint4|  
|unorm —|unorm_2 —<br /><br /> unorm2|unorm_3 —<br /><br /> unorm3|unorm_4 —<br /><br /> unorm4|  
  
### <a name="operators"></a>Operatory  
 Jeśli operator jest zdefiniowany między dwoma wektorami krótkie, jest także zdefiniowana między krótkich wektora i wartością skalarną. Ponadto te muszą być spełnione:  
  
-   Typ scalar musi być taki sam jak typ elementu krótkich wektora.  
  
-   Typ scalar może być niejawnie przekonwertowana na typ elementu vector przy użyciu tylko jedna konwersja zdefiniowana przez użytkownika.  
  
 Wykonywane są component-wise między każdego składnika krótkich wektora i skalarnych. Poniżej przedstawiono prawidłowe operatory:  
  
|Typ operatora|Prawidłowe typy|  
|-------------------|-----------------|  
|Operatory binarne|Prawidłowy na wszystkich typach: +, -, *, /,<br /><br /> Nieprawidłowa na typy całkowite: %, ^, &#124; &, <\<, >><br /><br /> Dwa wektory muszą mieć ten sam rozmiar, a wynik jest wektorem o tej samej wielkości.|  
|Operatory relacyjne|Prawidłowy na wszystkich typach: == i! =|  
|Przydział złożony — operator|Prawidłowy na wszystkich typach: +=,-=, * = / =<br /><br /> Nieprawidłowa na typy całkowite: % =, ^ =, &#124; = &, =, <\<=, >> =|  
|Operatory inkrementacji i dekrementacji|Prawidłowy na wszystkich typach: ++,--<br /><br /> Zarówno prefiks i przyrostek są prawidłowe.|  
|Bitowy operator NOT (~)|Prawidłowy na typy całkowite.|  
|Jednoargumentowy - — operator|Prawidłowy dla wszystkich typów, z wyjątkiem `unorm` i `uint`.|  
  
### <a name="swizzling-expressions"></a>Wyrażenia swizzling  
 Obsługuje krótkich biblioteki wektor `vector_type.identifier` konstrukcja akcesor dostęp do składników krótkich wektora. `identifier`, Czyli tzw. *wyrażenie swizzling*, określa składniki wektora. Wyrażenie może być wartością l-value lub r. Znaki w identyfikatorze może być: x, y, z i w; lub r, g, b, a. "x" i "r" oznacza składnik zero-ty percentyl, "y" i "g" Średnia pierwszy składnik i tak dalej. (Powiadomienia "x" i "r" nie można użyć w tym samym identyfikatorze.) W związku z tym "rgba" i "xyzw" zwraca ten sam rezultat. Metody dostępu jeden składnik, takie jak "x" i "y" typy wartości skalarnej. Składnik wielu metod dostępu są typami wektorów krótki. Na przykład możesz utworzyć `int_4` wektor o nazwie `fourInts` , a następnie ma wartości 2, 4, 6 i 8, `fourInts.y` zwraca liczbę całkowitą 4 i `fourInts.rg` zwraca `int_2` obiekt zawierający wartości 2 i 4.  
  
## <a name="texture-classes"></a>Klasy tekstury  
 Wiele procesorów graficznych są sprzętowe i pamięci podręczne zoptymalizowanych można pobrać pikseli i tekseli i renderowanie obrazów i tekstury. [Tekstury\<T, N >](../../parallel/amp/reference/texture-class.md) klasy, która jest klasą kontenera obiektów teksela, ujawniającą funkcjonalność tekstury te GPU. Teksela można:  
  
-   `int`, `uint`, `float`, `double`, `norm`, Lub `unorm` skalarne.  
  
-   Wektor krótkich zawiera dwie lub cztery składniki. Jedynym wyjątkiem jest `double_4`, co jest niedozwolone.  
  
 `texture` Obiekt może mieć Rząd równy 1, 2 lub 3. `texture` Obiektu można przechwycić tylko przez odwołanie w wyrażeniu lambda wywołania `parallel_for_each`. Tekstura jest przechowywana na procesora GPU jako obiekty tekstury Direct3D. Aby uzyskać więcej informacji na temat tekstur i tekseli w Direct3D, zobacz [wprowadzenie do tekstury programu Direct3D 11](http://go.microsoft.com/fwlink/p/linkid=248502).  
  
 Używanego typu teksela może być jedną z wielu formatów tekstury, które są używane w programowania grafiki. Na przykład formatu RGBA można użyć 32-bitowy, z 8 bitów R, G, B i skalarne elementy. Sprzęt tekstury karty graficznej mogą uzyskiwać dostęp do poszczególnych elementów na podstawie formatu. Na przykład jeśli używasz formatu RGBA tekstury sprzętu można wyodrębnić każdy element 8-bitową w wersji 32-bitowej. W C++ AMP można ustawić bitów na skalarne elementu z teksela, dzięki czemu można automatycznie dostęp do poszczególnych elementów skalarne w kodzie, bez użycia przesunięcia bitowego.  
  
### <a name="instantiating-texture-objects"></a>Tworzenie wystąpień obiektów tekstury  
 Można zadeklarować obiektu tekstury bez inicjowania. Poniższy przykładowy kod deklaruje kilka obiektów tekstury.  
  
```cpp  
#include <amp.h>  
#include <amp_graphics.h>  
using namespace concurrency;  
using namespace concurrency::graphics;  
  
void declareTextures() {  
  
    // Create a 16-texel texture of int.   
    texture<int, 1> intTexture1(16);    
    texture<int, 1> intTexture2(extent<1>(16));   
  
    // Create a 16 x 32 texture of float_2.    
    texture<float_2, 2> floatTexture1(16, 32);    
    texture<float_2, 2> floatTexture2(extent<2>(16, 32));     
  
    // Create a 2 x 4 x 8 texture of uint_4.   
    texture<uint_4, 3> uintTexture1(2, 4, 8);    
    texture<uint_4, 3> uintTexture2(extent<3>(2, 4, 8));  
}  
  
```  
  
 Umożliwia także konstruktora zadeklarować i zainicjować `texture` obiektu. Poniższy przykład kodu tworzy `texture` obiektu z wektorem `float_4` obiektów. Liczba bitów na element skalarne ma ustawioną wartość domyślna. Nie można użyć tego konstruktora z `norm`, `unorm`, lub krótkich wektory `norm` i `unorm`, ponieważ nie mają domyślnej liczby bitów na element skalarne.  
  
```cpp  
#include <amp.h>  
#include <amp_graphics.h>  
#include <vector>  
using namespace concurrency;  
using namespace concurrency::graphics;  
  
void initializeTexture() {  
  
    std::vector<int_4> texels;  
    for (int i = 0; i < 768 * 1024; i++) {  
        int_4 i4(i, i, i, i);  
        texels.push_back(i4);  
    }  
  
texture<int_4, 2> aTexture(768, 1024, texels.begin(), texels.end());  
}  
```  
  
 Możesz również deklarować i zainicjować `texture` obiektu przy użyciu przeładowania konstruktora, pobierającej wskaźnik źródło danych, rozmiaru źródła danych w bajtach i liczba bitów na element skalarne.  
  
```cpp  
void createTextureWithBPC() { *// Create the source data.  
    float source[1024* 2];   
    for (int i = 0; i <1024* 2; i++) {  
    source[i] = (float)i;  
 }  
 *// Initialize the texture by using the size of source in bytes *// and bits per scalar element.  
    texture<float_2, 1> floatTexture(1024, source, (unsigned int)sizeof(source), 32U);

}  
```  
  
 Tekstury, w tym przykładzie są tworzone na domyślny widok domyślny akceleratora. Jeśli chcesz określić, można użyć innego przeciążenia metody konstruktora `accelerator_view` obiektu. Nie można utworzyć obiektu tekstury akceleratora procesora CPU.  
  
 Istnieje limit na rozmiar każdego wymiaru `texture` obiektów, jak pokazano w poniższej tabeli. Błąd czasu wykonywania jest generowany po przekroczeniu limitów.  
  
|Tekstura|Limit rozmiaru|  
|-------------|---------------------|  
|Tekstura\<T-1 >|16384|  
|Tekstura\<T, 2 >|16384|  
|Tekstura\<T, 2 >|2048|  
  
### <a name="reading-from-texture-objects"></a>Odczytywanie z obiektów tekstury  
 Można odczytywać `texture` obiektu za pomocą [texture::operator\[\]](reference/texture-class.md#operator_at), [tekstury:: operator() — Operator](reference/texture-class.md#operator_call), lub [texture::get—Metoda](reference/texture-class.md#get). Dwa operatory zwracają wartość, nie odwołanie. W związku z tym nie można zapisać do `texture` obiektu za pomocą `texture::operator\[\]`.  
  
```cpp  
void readTexture() {  
    std::vector<int_2> src;      
    for (int i = 0; i <16 *32; i++) {  
    int_2 i2(i, i);

    src.push_back(i2);

 }  
 
    std::vector<int_2> dst(16* 32);

    array_view<int_2, 2> arr(16, 32, dst);

    arr.discard_data();

 
    const texture<int_2, 2> tex9(16, 32, src.begin(), src.end());

    parallel_for_each(tex9.extent, [=, &tex9] (index<2> idx) restrict(amp) { *// Use the subscript operator.        
    arr[idx].x += tex9[idx].x; *// Use the function () operator.        
    arr[idx].x += tex9(idx).x; *// Use the get method.  
    arr[idx].y += tex9.get(idx).y; *// Use the function () operator.    
    arr[idx].y += tex9(idx[0], idx[1]).y;   
 });

 
    arr.synchronize();

} 
 
```  
  
 Poniższy przykład kodu pokazuje, jak przechowywać tekstury kanałów w krótkich wektora, a następnie przejść poszczególne elementy skalarne jako właściwości krótkich wektora.  
  
```cpp  
void UseBitsPerScalarElement() { *// Create the image data. *// Each unsigned int (32-bit) represents four 8-bit scalar elements(r,g,b,a values).  
    const int image_height = 16;  
    const int image_width = 16;  
    std::vector<unsigned int> image(image_height* image_width);

 
    extent<2> image_extent(image_height, image_width);

 *// By using uint_4 and 8 bits per channel, each 8-bit channel in the data source is *// stored in one 32-bit component of a uint_4.  
    texture<uint_4, 2> image_texture(image_extent, image.data(), image_extent.size()* 4U,  8U);

 *// Use can access the RGBA values of the source data by using swizzling expressions of the uint_4.  
    parallel_for_each(image_extent, 
 [&image_texture](index<2> idx) restrict(amp)   
 { *// 4 bytes are automatically extracted when reading.  
    uint_4 color = image_texture[idx];   
    unsigned int r = color.r;   
    unsigned int g = color.g;   
    unsigned int b = color.b;   
    unsigned int a = color.a;   
 });

}  
 
```  
  
 W poniższej tabeli wymieniono Nieprawidłowa liczba bitów na kanał dla każdego typu wektora sortowania.  
  
|Typ danych tekstury|Nieprawidłowa bitów na element skalarne|  
|-----------------------|-----------------------------------|  
|int, int_2 —, int_4 —<br /><br /> uint uint_2 —, uint_4 —|8, 16, 32|  
|int_3 —, uint_3 —|32|  
|Float, float_2 —, float_4 —|16, 32|  
|float_3 —|32|  
|double_2 — Double,|64|  
|normy norm_2 —, norm_4 —<br /><br /> unorm —, unorm_2 —, unorm —, 4|8, 16|  
  
### <a name="writing-to-texture-objects"></a>Zapisywanie obiektów tekstury  
 Użyj [texture::set](reference/texture-class.md#set) metodę, aby zapisać `texture` obiektów. Obiekt tekstury może być tylko do odczytu lub odczytu/zapisu. Dla obiekt tekstury, aby być do odczytu i zapisu muszą być spełnione następujące warunki:  

  
-   T ma tylko jeden składnik skalarne. (Krótka wektory są niedozwolone.)  
  
-   T nie jest `double`, `norm`, lub `unorm`.  
  
-   `texture::bits_per_scalar_element` Właściwości to 32.  
  
 Jeśli wszystkie trzy nie są spełnione, a następnie `texture` obiekt jest tylko do odczytu. Pierwsze dwa warunki są sprawdzane podczas kompilacji. Błąd kompilacji jest generowany, jeśli masz kod, który próbuje zapisać `readonly` obiektu tekstury. Warunek `texture::bits_per_scalar_element` została wykryta w czasie wykonywania i generuje środowiska uruchomieniowego [unsupported_feature —](../../parallel/amp/reference/unsupported-feature-class.md) wyjątek przy próbie zapisu tylko do odczytu `texture` obiektu.  
  
 Poniższy przykład kodu zapisuje wartości do obiektu tekstury.  
  
```cpp  
void writeTexture() {  
    texture<int, 1> tex1(16);

    parallel_for_each(tex1.extent, [&tex1] (index<1> idx) restrict(amp) {      
    tex1.set(idx, 0);

 });

 
}  
 
```  
  
### <a name="copying-texture-objects"></a>Kopiowanie obiektów tekstury  
 Możesz skopiować między obiektami tekstury za pomocą [kopiowania](reference/concurrency-namespace-functions-amp.md#copy) funkcji lub [copy_async —](reference/concurrency-namespace-functions-amp.md#copy_async) funkcji, jak pokazano w poniższym przykładzie kodu.  
  
```cpp  
void copyHostArrayToTexture() { *// Copy from source array to texture object by using the copy function.  
    float floatSource[1024* 2];   
    for (int i = 0; i <1024* 2; i++) {  
    floatSource[i] = (float)i;  
}  
    texture<float_2, 1> floatTexture(1024);

    copy(floatSource, (unsigned int)sizeof(floatSource), floatTexture);

 *// Copy from source array to texture object by using the copy function.  
    char charSource[16* 16];   
    for (int i = 0; i <16* 16; i++) {  
    charSource[i] = (char)i;  
 }  
    texture<int, 2> charTexture(16, 16, 8U);

    copy(charSource, (unsigned int)sizeof(charSource), charTexture);
*// Copy from texture object to source array by using the copy function.  
    copy(charTexture, charSource, (unsigned int)sizeof(charSource));

}  
 
```  
  
 Ponadto można kopiować z jedną teksturę do drugiego za pomocą [texture::copy_to](reference/texture-class.md#copy_to) metody. W różnych accelerator_views może być dwa tekstury. Po skopiowaniu `writeonly_texture_view` object, dane są kopiowane do odpowiadającego `texture` obiektu. Liczba bitów na element skalarne i zakres musi być takie same na serwerze źródłowym i docelowym `texture` obiektów. Jeśli te wymagania nie są spełnione, środowisko uruchomieniowe zgłasza wyjątek.  

  
## <a name="texture-view-classes"></a>Klasy widoku tekstury  
 Wprowadza C++ AMP [texture_view — klasa](../../parallel/amp/reference/texture-view-class.md) w [!INCLUDE[vs_dev12](../../atl-mfc-shared/includes/vs_dev12_md.md)]. Widoki tekstury obsługują te same typy teksela i rangi jako [texture — klasa](../../parallel/amp/reference/texture-class.md), lecz w odróżnieniu od tekstury, zapewniają dostęp do sprzętu dodatkowe funkcje, takie jak próbkowania tekstury i mipmapy. Widoki tekstury obsługuje dostęp tylko do odczytu, tylko do zapisu i odczytu i zapisu w danych źródłowych tekstury.  
  
-   Dostęp tylko do odczytu są dostarczane przez `texture_view<const T, N>` specjalizacja szablonu, który obsługuje elementów, które mają 1, 2 lub 4 składników, texture próbkowanie i dynamicznych dostępu na różnych poziomach mipmap, które są ustalane w momencie wystąpienia widoku.  
  
-   Dostęp tylko do zapisu pochodzi od klasy niespecjalizowanej szablonu `texture_view<T, N>`, który obsługuje elementy, 2 lub 4 składników, które mogą uzyskiwać dostęp do jednego poziomu mipmapowania, który stwierdził, gdy wystąpienia widoku. Nie obsługuje pobierania próbek.  
  
-   Dostęp do odczytu i zapisu pochodzi od klasy niespecjalizowanej szablonu `texture_view<T, N>`, który, takie jak tekstury, obsługuje elementów, które mają tylko jeden składnik; widoku mogą uzyskiwać dostęp do jednego poziomu mipmapowania, który stwierdził, gdy zostanie on uruchomiony. Nie obsługuje pobierania próbek.  
  
 Widoki tekstury są podobne do macierzy, widoków, ale nie zapewniają funkcje zarządzania i ruchu danych który [array_view — klasa](../../parallel/amp/reference/array-view-class.md) udostępnia w porównaniu z [array — klasa](../../parallel/amp/reference/array-class.md). A `texture_view` można uzyskać tylko w widoku akceleratora lokalizację danych tekstury.  
  
### <a name="writeonlytextureview-deprecated"></a>writeonly_texture_view uznane za przestarzałe  
 Aby uzyskać [!INCLUDE[vs_dev12](../../atl-mfc-shared/includes/vs_dev12_md.md)], C++ AMP wprowadza lepszą obsługę funkcji tekstury sprzętu, takich jak pobieranie próbek i mipmapy, który nie jest obsługiwany przez [writeonly_texture_view — klasa](../../parallel/amp/reference/writeonly-texture-view-class.md). Nowo wprowadzonych `texture_view` klasa obsługuje podzbiorem funkcji w `writeonly_texture_view`; w związku z tym `writeonly_texture_view` jest przestarzały.  
  
 Firma Microsoft zaleca — co najmniej dla nowego kodu — używanej `texture_view` do funkcji dostępu, który został wcześniej dostarczony przez `writeonly_texture_view`. Porównaj w poniższych przykładach dwóch kodu, które zapisać obiekt tekstury, który zawiera dwa składniki (int_2 —). Zwróć uwagę, że w obu przypadkach widoku, `wo_tv4`, muszą zostać przechwycone przez wartość w wyrażeniu lambda. Oto przykład, który korzysta z nowych `texture_view` klasy:  
  
```cpp  
void write2ComponentTexture() {  
    texture<int_2, 1> tex4(16);

    texture_view<int_2, 1> wo_tv4(tex4);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {  
    wo_tv4.set(idx, int_2(1, 1));

 });

}  
```  
  
 A Oto przestarzałe `writeonly_texture_view` klasy:  
  
```  
void write2ComponentTexture() {  
    texture<int_2, 1> tex4(16);

    writeonly_texture_view<int_2, 1> wo_tv4(tex4);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {     
    wo_tv4.set(idx, int_2(1, 1));

 });

}  
```  
  
 Jak widać, przykłady kodu dwóch są niemal identyczne podczas zapisywania wszystkich operacji poziomu mipmapowania podstawowego. Jeśli używasz `writeonly_texture_view` w istniejącym kodem, a nie planowane jest zwiększają się, że kod, nie trzeba go zmienić. Jednak jeśli myślisz o wprowadzenia kodu do przodu, zalecamy użycie przepisywania `texture_view` ponieważ ulepszenia w nim obsługuje nowe funkcje tekstury sprzętu. Dowiedz się więcej informacji na temat nowych funkcji.  
  
 Aby uzyskać więcej informacji na temat amortyzacja `writeonly_texture_view`, zobacz [omówienie tekstury widok projektu w języku C++ AMP](http://blogs.msdn.com/b/nativeconcurrency/archive/2013/07/25/overview-of-the-texture-view-design-in-c-amp.aspx) na Programowanie równoległe w blogu kodu natywnego.  
  
### <a name="instantiating-texture-view-objects"></a>Tworzenie wystąpień obiektów widoku tekstury  
 Deklarowanie `texture_view` jest podobny do deklarowania `array_view` skojarzony z `array`. Poniższy przykładowy kod deklaruje kilka `texture` obiektów i `texture_view` obiektów skojarzonych z nimi.  
  
```  
#include <amp.h>  
#include <amp_graphics.h>  
using namespace concurrency;  
using namespace concurrency::graphics;  
  
void declareTextureViews()  
{  
    // Create a 16-texel texture of int, with associated texture_views.  
    texture<int, 1> intTexture(16);  
    texture_view<const int, 1> intTextureViewRO(intTexture);  // read-only  
    texture_view<int, 1> intTextureViewRW(intTexture);        // read-write  
  
    // Create a 16 x 32 texture of float_2, with associated texture_views.  
    texture<float_2, 2> floatTexture(16, 32);  
    texture_view<const float_2, 2> floatTextureViewRO(floatTexture);  // read-only  
    texture_view<float_2, 2> floatTextureViewRO(floatTexture);        // write-only  
  
    // Create a 2 x 4 x 8 texture of uint_4, with associated texture_views.  
    texture<uint_4, 3> uintTexture(2, 4, 8);  
    texture_view<const uint_4, 3> uintTextureViewRO(uintTexture);  // read-only  
    texture_view<uint_4, 3> uintTextureViewWO(uintTexture);        // write-only  
}  
```  
  
 Jak tekstury wyświetlić o typie elementu nie jest wartością stałą i ma jeden składnik jest do odczytu / zapisu, ale widoku tekstury, której typ elementów nie jest wartością stałą, ale ma więcej niż jeden componenent są tylko do zapisu. Widoki tekstury const typów elementów zawsze są tylko do odczytu, ale jeśli typ elementu nie jest wartością stałą, liczbę składników w elemencie Określa, czy jest ono odczytu i zapisu (część 1) lub w trybie tylko do zapisu (wiele składników).  
  
 Typ elementu `texture_view`— jego stałość, a także liczbę składników ma ona — także pełni rolę w określeniu, czy widok obsługuje próbkowania tekstury i jak dostępne poziomy mipmap:  
  
|Typ|Składniki|Odczyt|Write|Pobierania próbek|Mipmap dostępu|  
|----------|----------------|----------|-----------|--------------|-------------------|  
|texture_view\<const T, N >|1, 2, 4|Tak|Nie (1)|Tak|Tak, które można indeksować. Zakres jest określany przy tworzeniu wystąpienia.|  
|Texture_view\<T, N >|1<br /><br /> 2, 4|Tak<br /><br /> Nie (2)|Tak<br /><br /> Tak|Nie (1)<br /><br /> Nie (1)|Tak — jeden poziom. Poziom jest określany przy tworzeniu wystąpienia.<br /><br /> Tak — jeden poziom. Poziom jest określany przy tworzeniu wystąpienia.|  
  
 Z tej tabeli widać, że widoki tekstury tylko do odczytu obsługują w pełni nowe funkcje w zamian nie będą mogli zapisać do widoku. Widoki tekstury zapisu są ograniczone, w tym ich ma dostęp tylko do jednego poziomu mipmapowania. Widoki tekstury odczytu i zapisu są bardziej skomplikowane niż te zapisywalny, ponieważ ich dodać wymaganie, że typ elementu w widoku tekstury ma tylko jeden składnik. Zwróć uwagę, że próbkowanie nie jest obsługiwane dla widoków zapisywalny tekstury, ponieważ jest to operacja zorientowane na odczyt.  
  
### <a name="reading-from-texture-view-objects"></a>Odczytywanie z tekstury obiekty widoku  
 Odczytywanie danych unsampled tekstury za pośrednictwem widoku tekstury jest podobnie jak odczycie tekstury, ale tekstury są przechwytywane przez odwołanie, podczas gdy tekstury widoki są przechwytywane przez wartość. W poniższych przykładach dwóch kodu pokazano; pierwszy przy użyciu `texture` tylko:  
  
```  
void write2ComponentTexture() {  
    texture<int_2, 1> text_data(16);

    parallel_for_each(extent<1>(16), [&] (index<1> idx) restrict(amp) {  
    tex_data.set(idx, int_2(1, 1));

 });

}  
```  
  
 A Oto tym samym przykładzie, z wyjątkiem teraz używa `texture_view` klasy:  
  
```  
void write2ComponentTexture() {  
    texture<int_2, 1> tex_data(16);

    texture_view<int_2, 1> tex_view(tex_data);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {  
    tex_view.set(idx, int_2(1, 1));

 });

}  
```  
 Texture widoków, której elementy są oparte na typów zmiennoprzecinkowych — na przykład, float, float_2 — lub float_4 — — również można odczytu za pomocą próbkowania tekstury mógł korzystać z obsługi sprzętowej dla różnych trybach filtrowania i adresowania tryby. C++ AMP obsługuje dwa tryby filtrowania, które są najbardziej rozpowszechnione w scenariuszach obliczeniowych — punkt filtrowania (najbliższego sąsiada) i liniowej filtrowania (średnią ważoną) — i czterech trybów adresowania — zawijany, dublowane zablokowane za pomocą i obramowania. Aby uzyskać więcej informacji na temat trybów adresowania, zobacz [address_mode — wyliczenie](reference/concurrency-graphics-namespace-enums.md#address_mode).  
  
 Oprócz tryby, które C++ AMP nie obsługuje bezpośrednio mogą korzystać inne tryby filtrowania i adresowania trybów podstawowej platformy za pomocą międzyoperacyjnego interfejsów API do przyjęcia przykłady tekstury, który został utworzony przy użyciu interfejsów API platformy bezpośrednio. Na przykład Direct3D obsługuje inne tryby filtrowania, takie jak anizotropowej filtrowania i może dotyczyć innej Tryb adresowania każdego wymiaru tekstury. Można utworzyć próbnika opakowane w pionie, dublowane poziomo i próbkowany których współrzędne tekstury z anizotropowej filtrowanie przy użyciu interfejsów API Direct3D, a następnie korzystać próbnika w kodzie C++ AMP, przy użyciu `make_sampler` międzyoperacyjnego interfejsu API. Aby uzyskać więcej informacji, zobacz [tekstury próbkowania w C++ AMP](http://blogs.msdn.com/b/nativeconcurrency/archive/2013/07/18/texture-sampling-in-c-amp.aspx) na Programowanie równoległe w blogu kodu natywnego.  
  
 Widoki tekstury również obsługiwać odczyt mipmapy. Widoki tekstury tylko do odczytu (te, które ma stałą typu elementu) oferują większą elastyczność, ponieważ zakres MCI-poziomy, które jest określane przy tworzeniu wystąpienia może być próbkowany dynamicznie i elementów, które mają 1, 2 lub 4 składniki są obsługiwane. Widoki tekstury odczytu i zapisu, które mają elementy, które mają jeden składnik obsługuje również mipmapy, ale tylko z poziomu, który jest określany przy tworzeniu wystąpienia. Aby uzyskać więcej informacji, zobacz [tekstury z mipmapy](http://blogs.msdn.com/b/nativeconcurrency/archive/2013/08/22/texture-with-mipmaps.aspx) na Programowanie równoległe w blogu kodu natywnego.  
  
### <a name="writing-to-texture-view-objects"></a>Zapisywanie tekstury obiekty widoku  
 Użyj [texture_view::get — metoda](reference/texture-view-class.md#get) można zapisać do odpowiadającego `texture` za pośrednictwem `texture_view` obiektu. Widok tekstury jest tylko do odczytu, zapisu i odczytu lub tylko do zapisu. Aby mieć możliwość zapisu w widoku tekstury musi mieć typ elementu, który nie jest wartością stałą; dla widoku tekstury być zdatny do odczytu i zapisu jego typ elementu musi mieć tylko jeden składnik. W przeciwnym razie widok tekstury jest tylko do odczytu. Można tylko dostęp do jednego poziomu mipmapowania tekstury jednocześnie za pośrednictwem widoku tekstury, a podczas tworzenia wystąpienia klasy widoku określono poziom.  
  
 W tym przykładzie pokazano, jak można zapisać poziomu mipmapowania szczegółowe większość sekundy, zawierający 4 poziomy mipmap tekstury. Najbardziej szczegółowy poziomu mipmapowania jest poziom 0.  
  
```  
// Create a texture that has 4 mipmap levels : 16x16, 8x8, 4x4, 2x2  
texture<int, 2> tex(extent<2>(16, 16), 16U, 4);

 
// Create a writable texture view to the second mipmap level :4x4  
texture_view<int, 2> w_view(tex, 1);

 
parallel_for_each(w_view.extent, [=](index<2> idx) restrict(amp)  
{  
    w_view.set(idx, 123);

});
```  
  
## <a name="interoperability"></a>Współdziałanie  

 Współdziałanie obsługuje środowiska uruchomieniowego C++ AMP `texture<T,1>` i [interfejsu ID3D11Texture1D](http://go.microsoft.com/fwlink/p/LinkId=248503), między `texture<T,2>` i [interfejsu ID3D11Texture2D](http://go.microsoft.com/fwlink/p/LinkId=255317)oraz między `texture<T,3>`i [ID3D11Texture3D interfejsu](http://go.microsoft.com/fwlink/p/LinkId=255377). [Get_texture —](reference/concurrency-graphics-direct3d-namespace-functions.md#get_texture) ma metodę `texture` obiektu i zwraca `IUnknown` interfejsu. [Make_texture —](reference/concurrency-graphics-direct3d-namespace-functions.md#make_texture) ma metodę `IUnknown` interfejsu i `accelerator_view` obiektu i zwraca `texture` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [double_2 — klasa](../../parallel/amp/reference/double-2-class.md)   
 [double_3 — klasa](../../parallel/amp/reference/double-3-class.md)   
 [double_4 — klasa](../../parallel/amp/reference/double-4-class.md)   
 [float_2 — klasa](../../parallel/amp/reference/float-2-class.md)   
 [float_3 — klasa](../../parallel/amp/reference/float-3-class.md)   
 [float_4 — klasa](../../parallel/amp/reference/float-4-class.md)   
 [int_2 — klasa](../../parallel/amp/reference/int-2-class.md)   
 [int_3 — klasa](../../parallel/amp/reference/int-3-class.md)   
 [int_4 — klasa](../../parallel/amp/reference/int-4-class.md)   
 [norm_2 — klasa](../../parallel/amp/reference/norm-2-class.md)   
 [norm_3 — klasa](../../parallel/amp/reference/norm-3-class.md)   
 [norm_4 — klasa](../../parallel/amp/reference/norm-4-class.md)   
 [short_vector — struktura](../../parallel/amp/reference/short-vector-structure.md)   
 [short_vector_traits — struktura](../../parallel/amp/reference/short-vector-traits-structure.md)   
 [uint_2 — klasa](../../parallel/amp/reference/uint-2-class.md)   
 [uint_3 — klasa](../../parallel/amp/reference/uint-3-class.md)   
 [uint_4 — klasa](../../parallel/amp/reference/uint-4-class.md)   
 [unorm_2 — klasa](../../parallel/amp/reference/unorm-2-class.md)   
 [unorm_3 — klasa](../../parallel/amp/reference/unorm-3-class.md)   
 [unorm_4 — klasa](../../parallel/amp/reference/unorm-4-class.md)
