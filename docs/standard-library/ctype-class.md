---
title: "CType — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xlocale/std::ctype
- xlocale/std::ctype::char_type
- xlocale/std::ctype::do_is
- xlocale/std::ctype::do_narrow
- xlocale/std::ctype::do_scan_is
- xlocale/std::ctype::do_scan_not
- xlocale/std::ctype::do_tolower
- xlocale/std::ctype::do_toupper
- xlocale/std::ctype::do_widen
- xlocale/std::ctype::is
- xlocale/std::ctype::narrow
- xlocale/std::ctype::scan_is
- xlocale/std::ctype::scan_not
- xlocale/std::ctype::tolower
- xlocale/std::ctype::toupper
- xlocale/std::ctype::widen
dev_langs: C++
helpviewer_keywords:
- std::ctype [C++]
- std::ctype [C++], char_type
- std::ctype [C++], do_is
- std::ctype [C++], do_narrow
- std::ctype [C++], do_scan_is
- std::ctype [C++], do_scan_not
- std::ctype [C++], do_tolower
- std::ctype [C++], do_toupper
- std::ctype [C++], do_widen
- std::ctype [C++], is
- std::ctype [C++], narrow
- std::ctype [C++], scan_is
- std::ctype [C++], scan_not
- std::ctype [C++], tolower
- std::ctype [C++], toupper
- std::ctype [C++], widen
ms.assetid: 3627154c-49d9-47b5-b28f-5bbedee38e3b
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 10bc57e29383386df63de4cd6f27299a8f9986a6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ctype-class"></a>ctype — Klasa
Klasa zawierająca zestaw reguł, który służy do klasyfikowania znaków, konwersji z wielkich i małych liter i konwersji między macierzystym zestawem znaków i zestawem używanym przez ustawienia regionalne.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class CharType>  
class ctype : public ctype_base;  
```  
  
#### <a name="parameters"></a>Parametry  
 `CharType`  
 Typ używany w programie do kodowania znaków.  
  
## <a name="remarks"></a>Uwagi  
 Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba jej wartości przechowywanej dostępu są przechowywane w unikatową wartość dodatnią **identyfikator.** Do kryteriów klasyfikacji jest dostarczany typ zagnieżdżonej maski bitów w klasie podstawowej ctype_base.  
  
 Standardowa biblioteka C++ definiuje dwie jawne specjalizacje tej klasy szablonu:  
  
- [CType —](../standard-library/ctype-char-class.md)< `char`>, jawnej specjalizacji różnice, w których opisano oddzielnie.  
  
- **CType —**< `wchar_t`>, która traktuje jako znaki dwubajtowe elementów.  
  
 Inne specjalizacji szablonu klasy **ctype** \< **CharType**>:  
  
-   Konwersja wartości ***ch*** typu **CharType** wartość typu `char` z wyrażeniem ( `char`) **ch**.  
  
-   Konwersja wartości ***bajtów*** typu `char` wartość typu **CharType** za pomocą wyrażenia **CharType** ( **bajtów**).  
  
 Wszystkie inne operacje są wykonywane na `char` wartości w taki sam sposób jak w przypadku jawna specjalizacja **ctype**< `char`>.  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[CType —](#ctype)|Konstruktor dla obiektów klasy `ctype` obsługujących jako aspekty ustawień regionalnych dla znaków.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#char_type)|Typ, który opisuje znak używany przez ustawienie regionalne.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[do_is](#do_is)|Funkcja wirtualna wywoływana w celu sprawdzenia, czy pojedynczy znak ma określony atrybut, lub sklasyfikowania atrybutów każdego znaku w zakresie i przechowywania ich w tablicy.|  
|[do_narrow](#do_narrow)|Wywołuje funkcję wirtualną do konwersji znaków typu `CharType` używane przez ustawienia regionalne do odpowiedniego znaku typu `char` zestawu w macierzystym znaków.|  
|[do_scan_is](#do_scan_is)|Wirtualna funkcja wywoływana w celu zlokalizowania pierwszego znaku w zakresie, który pasuje do określonej maski.|  
|[do_scan_not](#do_scan_not)|Funkcja wirtualna wywoływana w celu zlokalizowania pierwszego znaku w zakresie, który nie pasuje do określonej maski.|  
|[do_tolower](#do_tolower)|Funkcja wirtualna wywoływana w celu konwersji znaku lub zakresu znaków na ich małe litery.|  
|[do_toupper](#do_toupper)|Funkcja wirtualna wywoływana w celu konwersji znaku lub zakresu znaków na ich wielkie litery.|  
|[do_widen](#do_widen)|Wywołuje się, by funkcję wirtualną konwertuje znak typu `char` zestawu do odpowiedniego znaku typu natywnego znaków `CharType` używane przez ustawień regionalnych.|  
|[jest](#is)|Sprawdza, czy pojedynczy znak ma określony atrybut, lub klasyfikuje atrybuty każdego znaku w zakresie i przechowuje je w tablicy.|  
|[zawęzić](#narrow)|Konwertuje znak typu `CharType` używane przez ustawień regionalnych na odpowiedni znak Typ char w zestawie znaków macierzystego.|  
|[scan_is](#scan_is)|Lokalizuje pierwszy znak w zakresie, który pasuje do określonej maski.|  
|[scan_not](#scan_not)|Lokalizuje pierwszy znak w zakresie, który nie pasuje do określonej maski.|  
|[tolower](#tolower)|Konwertuje znak lub zakres znaków na małe litery.|  
|[toupper](#toupper)|Konwertuje znak lub zakres znaków na wielkie litery.|  
|[rozszerzenia](#widen)|Konwertuje znak typu `char` zestawu do odpowiedniego znaku typu natywnego znaków `CharType` używane przez ustawień regionalnych.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<ustawień regionalnych >  
  
 **Namespace:** Standard  
  
##  <a name="char_type"></a>CType::char_type  
 Typ, który opisuje znak używany przez ustawienie regionalne.  
  
```  
typedef CharType char_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem parametru szablonu **CharType**.  
  
### <a name="example"></a>Przykład  
  Zobacz opis funkcji Członkowskich [poszerzyć](#widen) na przykład, który używa `char_type` jako do wartości zwracanej.  
  
##  <a name="ctype"></a>CType::CType  
 Konstruktor dla obiektów klasy ctype służyć jako aspekty ustawień regionalnych dla znaków.  
  
```  
explicit ctype(size_t _Refs = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `_Refs`  
 Wartość całkowita używany do określania typu zarządzania pamięci dla obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Możliwe wartości `_Refs` i ich znaczenie są:  
  
-   0: okres istnienia obiektu zarządza ustawieniami regionalnymi, które zawierałoby proces.  
  
-   1: okres istnienia obiektu musi być zarządzane ręcznie.  
  
-   \>1: te wartości są niezdefiniowane.  
  
 Nie bezpośredniego przykładów to możliwe, ponieważ destruktor jest chroniony.  
  
 Konstruktor inicjuje jego `locale::facet` obiektu podstawowego z **locale::**[aspektu](../standard-library/locale-class.md#facet_class)( `_Refs`).  
  
##  <a name="do_is"></a>CType::do_is  
 Funkcja wirtualna wywoływana w celu sprawdzenia, czy pojedynczy znak ma określony atrybut, lub sklasyfikowania atrybutów każdego znaku w zakresie i przechowywania ich w tablicy.  
  
```  
virtual bool do_is(
    mask maskVal,   
    CharType ch) const;

 
virtual const CharType *do_is(
    const CharType* first,   
    const CharType* last,  
    mask* dest) const;
```  
  
### <a name="parameters"></a>Parametry  
 `maskVal`  
 Wartość maski, dla którego ma zostać przetestowana znak.  
  
 `ch`  
 Znak, w których atrybuty do sprawdzenia.  
  
 `first`  
 Wskaźnik do pierwszego znaku w zakresie, w których atrybuty mają być klasyfikowane.  
  
 `last`  
 Wskaźnik do znaku bezpośrednio po ostatnim znakiem w zakresie, w których atrybuty mają być klasyfikowane.  
  
 `dest`  
 Wskaźnik do początku tablicy, w którym mają być przechowywane wartości maski charakteryzujące atrybuty znaków.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy funkcji członkowskiej zwraca wartość logiczną, która jest **true** Jeśli znak przetestowane ma atrybut opisanego przez wartość maski; **false** Jeśli go nie ma atrybutu.  
  
 Drugi funkcji członkowskiej zwraca tablicę zawierającą wartości maski charakteryzujące atrybuty znaków w zakresie.  
  
### <a name="remarks"></a>Uwagi  
 Wartości maski klasyfikowania atrybutów znaki są udostępniane przez klasę [ctype_base —](../standard-library/ctype-base-class.md), z których ctype pochodzi. Pierwszy funkcji członkowskiej może akceptować wyrażenia jej pierwszy parametr nazywany masek bitowych i utworzony z kombinacji wartości maski bitowe operatory logiczne (&#124; &, ^, ~).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [jest](#is), które wywołuje `do_is`.  
  
##  <a name="do_narrow"></a>CType::do_narrow  
 Wywołuje funkcję wirtualną do konwersji znaków typu `CharType` używane przez ustawienia regionalne do odpowiedniego znaku typu `char` zestawu w macierzystym znaków.  
  
```  
virtual char do_narrow(
    CharType ch,   
    char default = '\0') const;

 
virtual const CharType* do_narrow(
    const CharType* first,   
    const CharType* last,  
    char default,   
    char* dest) const;
```  
  
### <a name="parameters"></a>Parametry  
 `ch`  
 Znak typu `Chartype` używane przez ustawienia regionalne do skonwertowania.  
  
 `default`  
 Wartość domyślna ma być przypisany przez funkcję elementu członkowskiego znaków typu `CharType` nie mają odpowiednika znaków typu `char`.  
  
 `first`  
 Wskaźnik do pierwszego znaku w zakresie znaków ma zostać przekonwertowany.  
  
 `last`  
 Wskaźnik do znaku bezpośrednio po ostatnim znakiem w zakresie znaków ma zostać przekonwertowany.  
  
 `dest`  
 Const wskaźnik do pierwszego znaku typu `char` w zakres docelowy przechowujący przekonwertowanego zakres znaków.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszej funkcji chroniony element członkowski zwraca znak natywnego typu CHAR, która odpowiada na znak parametru typu `CharType` lub `default` Jeśli zdefiniowano odpowiednika.  
  
 Druga funkcja chroniony element członkowski zwraca wskaźnik do zakresu docelowego natywnego znaków, znaków typu `CharType`.  
  
### <a name="remarks"></a>Uwagi  
 Drugi chronionego elementu członkowskiego szablonu funkcji magazynów w `dest`[ `I`] wartości `do_narrow`( `first` [ `I`], `default`), dla `I` w zakresie [0, `last`  -  `first`).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [zawęzić](#narrow), które wywołuje `do_narrow`.  
  
##  <a name="do_scan_is"></a>CType::do_scan_is  
 Wirtualna funkcja wywoływana w celu zlokalizowania pierwszego znaku w zakresie, który pasuje do określonej maski.  
  
```  
virtual const CharType *do_scan_is(
    mask maskVal,   
    const CharType* first,   
    const CharType* last) const;
```  
  
### <a name="parameters"></a>Parametry  
 `maskVal`  
 Wartość maski można dopasować znakiem.  
  
 `first`  
 Wskaźnik do pierwszego znaku w zakresie do przeskanowania.  
  
 `last`  
 Wskaźnik do znaku bezpośrednio po ostatnim znakiem w zakresie do skanowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do pierwszego znaku w zakresie, który jest zgodny z określonym maski. Jeśli takie wartość nie istnieje, funkcja zwraca`last.`  
  
### <a name="remarks"></a>Uwagi  
 Funkcja chroniony element członkowski zwraca najmniejszą wskaźnika `ptr` z zakresu [ `first`, `last`) dla której [do_is](#do_is)( `maskVal`, * `ptr`) ma wartość true.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [scan_is](#scan_is), które wywołuje `do_scan_is`.  
  
##  <a name="do_scan_not"></a>CType::do_scan_not  
 Funkcja wirtualna wywoływana w celu zlokalizowania pierwszego znaku w zakresie, który nie pasuje do określonej maski.  
  
```  
virtual const CharType *do_scan_not(
    mask maskVal,   
    const CharType* first,   
    const CharType* last) const;
```  
  
### <a name="parameters"></a>Parametry  
 `maskVal`  
 Wartość mask nie mają być dopasowywane znakiem.  
  
 `first`  
 Wskaźnik do pierwszego znaku w zakresie do przeskanowania.  
  
 `last`  
 Wskaźnik do znaku bezpośrednio po ostatnim znakiem w zakresie do skanowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do pierwszego znaku w zakresie określona maska jest zgodny. Jeśli takie wartość nie istnieje, funkcja zwraca `last`.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja chroniony element członkowski zwraca najmniejszą wskaźnika `ptr` z zakresu [ `first`, `last`) dla której [do_is](#do_is)( `maskVal`, * `ptr`) ma wartość false.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [scan_not](#scan_not), które wywołuje `do_scan_not`.  
  
##  <a name="do_tolower"></a>CType::do_tolower  
 Funkcję wirtualną o nazwie konwertowanie znak lub zakres znaków na małe litery.  
  
```  
virtual CharType do_tolower(CharType ch) const;

 
virtual const CharType *do_tolower(
    CharType* first,   
    const CharType* last) const;
```  
  
### <a name="parameters"></a>Parametry  
 `ch`  
 Znak, który ma zostać przekonwertowany na małe litery.  
  
 `first`  
 Wskaźnik do pierwszego znaku w zakresie znaków, których przypadków są do skonwertowania.  
  
 `last`  
 Wskaźnik do znaku bezpośrednio po ostatnim znakiem w zakresie znaków, których przypadków są do skonwertowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszej funkcji chroniony element członkowski zwraca małe formularza parametru `ch`. Jeśli istnieje żaden formularz małe litery, zwraca `ch`. Drugi chronionego elementu członkowskiego funkcja zwraca `last`.  
  
### <a name="remarks"></a>Uwagi  
 Drugi funkcji szablonu chroniony element członkowski zastępuje każdy element `first` [ `I`], dla `I` w zakresie [0, `last`  -  `first`), z `do_tolower`( `first` [ `I`]).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [tolower](#tolower), które wywołuje `do_tolower`.  
  
##  <a name="do_toupper"></a>CType::do_toupper  
 Funkcja wirtualna wywoływana w celu konwersji znaku lub zakresu znaków na ich wielkie litery.  
  
```  
virtual CharType do_toupper(CharType ch) const;

 
virtual const CharType *do_toupper(
    CharType* first,   
    const CharType* last) const;
```  
  
### <a name="parameters"></a>Parametry  
 `ch`  
 Znak, który ma zostać przekonwertowane na wielkie litery.  
  
 `first`  
 Wskaźnik do pierwszego znaku w zakresie znaków, których przypadków są do skonwertowania.  
  
 `last`  
 Wskaźnik do znaku bezpośrednio po ostatnim znakiem w zakresie znaków, których przypadków są do skonwertowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwsza funkcja chroniony element członkowski zwraca wielkich liter parametru `ch`. Jeśli istnieje nie wielkich liter, zwraca `ch`. Drugi chronionego elementu członkowskiego funkcja zwraca `last`.  
  
### <a name="remarks"></a>Uwagi  
 Drugi funkcji szablonu chroniony element członkowski zastępuje każdy element `first` [ `I`], dla `I` w zakresie [0, `last`  -  `first`), z `do_toupper`( `first` [ `I`]).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [toupper](#toupper), które wywołuje `do_toupper`.  
  
##  <a name="do_widen"></a>CType::do_widen  
 Wywołuje się, by funkcję wirtualną konwertuje znak typu `char` zestawu do odpowiedniego znaku typu natywnego znaków `CharType` używane przez ustawień regionalnych.  
  
```  
virtual CharType do_widen(char byte) const;

 
virtual const char *do_widen(
    const char* first,   
    const char* last,   
    CharType* dest) const;
```  
  
### <a name="parameters"></a>Parametry  
 `byte`  
 Znak typu `char` natywnego zestawu do konwersji znaków.  
  
 `first`  
 Wskaźnik do pierwszego znaku w zakresie znaków ma zostać przekonwertowany.  
  
 `last`  
 Wskaźnik do znaku bezpośrednio po ostatnim znakiem w zakresie znaków ma zostać przekonwertowany.  
  
 `dest`  
 Wskaźnik do pierwszego znaku typu `CharType` w zakres docelowy przechowujący przekonwertowanego zakres znaków.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwsza funkcja chroniony element członkowski zwraca znak typu `CharType` odpowiadający znak parametru typu natywnego `char`.  
  
 Druga funkcja chroniony element członkowski zwraca wskaźnik do docelowy zakres znaków typu `CharType` używane przez ustawienia regionalne natywnego znaków typu `char`.  
  
### <a name="remarks"></a>Uwagi  
 Drugi chronionego elementu członkowskiego szablonu funkcji magazynów w `dest`[ `I`] wartości `do_widen`( `first`[ `I`]), dla `I` w zakresie [0, `last`  -  `first`).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [poszerzyć](#widen), które wywołuje `do_widen`.  
  
##  <a name="is"></a>CType::is  
 Sprawdza, czy pojedynczy znak lub ma określonego atrybutu klasyfikuje atrybuty dla każdego znaku zakresu i przechowuje je w tablicy.  
  
```  
bool is(mask maskVal, CharType ch) const;

 
const CharType *is(
    const CharType* first,   
    const CharType* last,  
    mask* dest) const;
```  
  
### <a name="parameters"></a>Parametry  
 `maskVal`  
 Wartość maski, dla którego ma zostać przetestowana znak.  
  
 `ch`  
 Znak, w których atrybuty do sprawdzenia.  
  
 `first`  
 Wskaźnik do pierwszego znaku w zakresie, w których atrybuty mają być klasyfikowane.  
  
 `last`  
 Wskaźnik do znaku bezpośrednio po ostatnim znakiem w zakresie, w których atrybuty mają być klasyfikowane.  
  
 `dest`  
 Wskaźnik do początku tablicy, w którym mają być przechowywane wartości maski charakteryzujące atrybuty znaków.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca pierwszy funkcji członkowskiej `true` Jeśli znak przetestowane ma atrybut opisanego przez wartość maski; `false` Jeśli go nie ma atrybutu.  
  
 Drugi funkcji członkowskiej zwraca wskaźnik do ostatni znak w zakresie, w których atrybuty mają być klasyfikowane.  
  
### <a name="remarks"></a>Uwagi  
 Wartości maski klasyfikowania atrybutów znaki są udostępniane przez klasę [ctype_base — klasa](../standard-library/ctype-base-class.md), z których ctype pochodzi. Pierwszy funkcji członkowskiej może akceptować wyrażenia jej pierwszy parametr nazywany masek bitowych i utworzony z kombinacji wartości maski bitowe operatory logiczne (&#124; &, ^, ~).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// ctype_is.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main() {  
   locale loc1 ( "German_Germany" ), loc2 ( "English_Australia" );  
  
   if (use_facet<ctype<char> > ( loc1 ).is( ctype_base::alpha, 'a' ))  
      cout << "The character 'a' in locale loc1 is alphabetic."   
           << endl;  
   else  
      cout << "The character 'a' in locale loc1 is not alphabetic."   
           << endl;  
  
   if (use_facet<ctype<char> > ( loc2 ).is( ctype_base::alpha, '!' ))  
      cout << "The character '!' in locale loc2 is alphabetic."   
           << endl;  
   else  
      cout << "The character '!' in locale loc2 is not alphabetic."   
           << endl;  
  
   char *string = "Hello, my name is John!";  
   ctype<char>::mask maskarray[30];  
   use_facet<ctype<char> > ( loc2 ).is(  
      string, string + strlen(string), maskarray );  
   for (unsigned int i = 0; i < strlen(string); i++) {  
      cout << string[i] << ": "  
           << (maskarray[i] & ctype_base::alpha  "alpha"  
                                                : "not alpha")  
           << endl;;  
   };  
}  
```  
  
##  <a name="narrow"></a>CType::Narrow  
 Konwertuje znaki typu `CharType` używane przez ustawienia regionalne odpowiadające im znaki typu `char` zestawu w macierzystym znaków.  
  
```  
char narrow(CharType ch, char default = '\0') const;

 
const CharType* narrow(
    const CharType* first,   
    const CharType* last,  
    char default,   
    char* dest) const;
```  
  
### <a name="parameters"></a>Parametry  
 `ch`  
 Znak typu `Chartype` używane przez ustawienia regionalne do skonwertowania.  
  
 `default`  
 Wartość domyślna ma być przypisany przez funkcję elementu członkowskiego znaków typu `CharType` nie mają odpowiednika znaków typu `char`.  
  
 `first`  
 Wskaźnik do pierwszego znaku w zakresie znaków ma zostać przekonwertowany.  
  
 `last`  
 Wskaźnik do znaku bezpośrednio po ostatnim znakiem w zakresie znaków ma zostać przekonwertowany.  
  
 `dest`  
 Const wskaźnik do pierwszego znaku typu `char` w zakres docelowy przechowujący przekonwertowanego zakres znaków.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy funkcji członkowskiej zwraca znak natywnego typu `char` odpowiadający znak parametru typu `CharType default` Jeśli odpowiednikiem nie jest zdefiniowany.  
  
 Drugi funkcji członkowskiej zwraca wskaźnik do zakresu docelowego natywnego znaków, znaków typu `CharType`.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca pierwszy funkcji członkowskiej [do_narrow](#do_narrow)( `ch`, `default`). Zwraca drugie funkcji członkowskiej [do_narrow](#do_narrow) ( `first`, `last`, `default`, `dest`). Tylko znaki podstawowe źródło dotrą do ma unikatowy obrazu odwrotny `CharType` w obszarze `narrow`. Te znaki podstawowe źródło zawiera następujące niezmiennej: `narrow` ( [poszerzyć](#widen) ( **c** ), 0) == **c**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// ctype_narrow.cpp  
// compile with: /EHsc /W3  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main( )  
{  
   locale loc1 ( "english" );  
   wchar_t *str1 = L"\x0392fhello everyone";  
   char str2 [16];  
   bool result1 = (use_facet<ctype<wchar_t> > ( loc1 ).narrow  
      ( str1, str1 + wcslen(str1), 'X', &str2[0] ) != 0);  // C4996  
   str2[wcslen(str1)] = '\0';  
   wcout << str1 << endl;  
   cout << &str2[0] << endl;  
}  
```  
  
```Output  
Xhello everyone  
```  
  
##  <a name="scan_is"></a>CType::scan_is  
 Lokalizuje pierwszy znak w zakresie, który pasuje do określonej maski.  
  
```  
const CharType *scan_is(
    mask maskVal,   
    const CharType* first,   
    const CharType* last) const;
```  
  
### <a name="parameters"></a>Parametry  
 `maskVal`  
 Wartość maski można dopasować znakiem.  
  
 `first`  
 Wskaźnik do pierwszego znaku w zakresie do przeskanowania.  
  
 `last`  
 Wskaźnik do znaku bezpośrednio po ostatnim znakiem w zakresie do skanowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do pierwszego znaku w zakresie, który jest zgodny z określonym maski. Jeśli takie wartość nie istnieje, funkcja zwraca`last.`  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca [do_scan_is](#do_scan_is)( `maskVal`, `first`, `last`).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// ctype_scan_is.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main( )     
{  
   locale loc1 ( "German_Germany" );  
  
   char *string = "Hello, my name is John!";  
  
   const char* i = use_facet<ctype<char> > ( loc1 ).scan_is  
      ( ctype_base::punct, string, string + strlen(string) );  
   cout << "The first punctuation is \"" << *i << "\" at position: "   
      << i - string << endl;  
}  
```  
  
```Output  
The first punctuation is "," at position: 5  
```  
  
##  <a name="scan_not"></a>CType::scan_not  
 Lokalizuje pierwszy znak w zakresie, który nie pasuje do określonej maski.  
  
```  
const CharType *scan_not(
    mask maskVal,   
    const CharType* first,   
    const CharType* last) const;
```  
  
### <a name="parameters"></a>Parametry  
 `maskVal`  
 Wartość mask nie mają być dopasowywane znakiem.  
  
 `first`  
 Wskaźnik do pierwszego znaku w zakresie do przeskanowania.  
  
 `last`  
 Wskaźnik do znaku bezpośrednio po ostatnim znakiem w zakresie do skanowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do pierwszego znaku w zakresie, który jest niezgodny z określonym maski. Jeśli takie wartość nie istnieje, funkcja zwraca `last`.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca [do_scan_not](#do_scan_not)( `maskVal`, `first`, `last`).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// ctype_scan_not.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main( )     
{  
   locale loc1 ( "German_Germany" );  
  
   char *string = "Hello, my name is John!";  
  
   const char* i = use_facet<ctype<char> > ( loc1 ).scan_not  
      ( ctype_base::alpha, string, string + strlen(string) );  
   cout << "First nonalpha character is \"" << *i << "\" at position: "   
      << i - string << endl;  
}  
```  
  
```Output  
First nonalpha character is "," at position: 5  
```  
  
##  <a name="tolower"></a>CType::tolower  
 Konwertuje znak lub zakres znaków na małe litery.  
  
```  
CharType tolower(CharType ch) const;

 
const CharType *tolower(CharType* first, const CharType* last) const;
```  
  
### <a name="parameters"></a>Parametry  
 `ch`  
 Znak, który ma zostać przekonwertowany na małe litery.  
  
 `first`  
 Wskaźnik do pierwszego znaku w zakresie znaków, których przypadków są do skonwertowania.  
  
 `last`  
 Wskaźnik do znaku bezpośrednio po ostatnim znakiem w zakresie znaków, których przypadków są do skonwertowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszej funkcji Członkowskich zwraca małe formularza parametru `ch`. Jeśli istnieje żaden formularz małe litery, zwraca `ch`.  
  
 Zwraca drugie funkcji członkowskiej `last`.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca pierwszy funkcji członkowskiej [do_tolower](#do_tolower)( `ch`). Zwraca drugie funkcji członkowskiej [do_tolower](#do_tolower)( `first`, `last`).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// ctype_tolower.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main( )  
{  
   locale loc1 ( "German_Germany" );  
  
   char string[] = "HELLO, MY NAME IS JOHN";  
  
   use_facet<ctype<char> > ( loc1 ).tolower  
      ( string, string + strlen(string) );  
   cout << "The lowercase string is: " << string << endl;  
}  
```  
  
```Output  
The lowercase string is: hello, my name is john  
```  
  
##  <a name="toupper"></a>CType::toupper  
 Konwertuje znak lub zakres znaków na wielkie litery.  
  
```  
CharType toupper(CharType ch) const; 
const CharType *toupper(CharType* first, const CharType* last) const;
```  
  
### <a name="parameters"></a>Parametry  
 `ch`  
 Znak, który ma zostać przekonwertowany na wielkie litery.  
  
 `first`  
 Wskaźnik do pierwszego znaku w zakresie znaków, których przypadków są do skonwertowania.  
  
 `last`  
 Wskaźnik do znaku bezpośrednio po ostatnim znakiem w zakresie znaków, których przypadków są do skonwertowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy funkcji członkowskiej zwraca wielkich liter parametru `ch`. Jeśli istnieje nie wielkich liter, zwraca `ch`.  
  
 Zwraca drugie funkcji członkowskiej `last`.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca pierwszy funkcji członkowskiej [do_toupper](#do_toupper)( `ch`). Zwraca drugie funkcji członkowskiej [do_toupper](#do_toupper)( `first`, `last`).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// ctype_toupper.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main( )     
{  
   locale loc1 ( "German_Germany" );  
  
   char string[] = "Hello, my name is John";  
  
   use_facet<ctype<char> > ( loc1 ).toupper  
      ( string, string + strlen(string) );  
   cout << "The uppercase string is: " << string << endl;  
}  
```  
  
```Output  
The uppercase string is: HELLO, MY NAME IS JOHN  
```  
  
##  <a name="widen"></a>CType::widen  
 Konwertuje znak typu `char` zestawu do odpowiedniego znaku typu natywnego znaków `CharType` używane przez ustawień regionalnych.  
  
```  
CharType widen(char byte) const; 
const char *widen(const char* first, const char* last, CharType* dest) const;
```  
  
### <a name="parameters"></a>Parametry  
 `byte`  
 Zestaw znaków typu CHAR natywnego znaków ma zostać przekonwertowany.  
  
 `first`  
 Wskaźnik do pierwszego znaku w zakresie znaków ma zostać przekonwertowany.  
  
 `last`  
 Wskaźnik do znaku bezpośrednio po ostatnim znakiem w zakresie znaków ma zostać przekonwertowany.  
  
 `dest`  
 Wskaźnik do pierwszego znaku typu `CharType` w zakres docelowy przechowujący przekonwertowanego zakres znaków.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy funkcji członkowskiej zwraca znak typu `CharType` odpowiadający znak parametru typu natywnego `char`.  
  
 Drugi funkcji członkowskiej zwraca wskaźnik do docelowy zakres znaków typu `CharType` używane przez ustawienia regionalne natywnego znaków typu `char`.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca pierwszy funkcji członkowskiej [do_widen](#do_widen)( `byte`). Zwraca drugie funkcji członkowskiej [do_widen](#do_widen)( `first`, `last`, `dest`).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// ctype_widen.cpp  
// compile with: /EHsc /W3  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main( )  
{  
   locale loc1 ( "English" );  
   char *str1 = "Hello everyone!";  
   wchar_t str2 [16];  
   bool result1 = (use_facet<ctype<wchar_t> > ( loc1 ).widen  
      ( str1, str1 + strlen(str1), &str2[0] ) != 0);  // C4996  
   str2[strlen(str1)] = '\0';  
   cout << str1 << endl;  
   wcout << &str2[0] << endl;  
  
   ctype<wchar_t>::char_type charT;  
   charT = use_facet<ctype<char> > ( loc1 ).widen( 'a' );  
}  
```  
  
```Output  
Hello everyone!  
Hello everyone!  
```  
  
## <a name="see-also"></a>Zobacz też  
 [\<Ustawienia regionalne >](../standard-library/locale.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

