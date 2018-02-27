---
title: Klasa platform::String | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::String::String
- VCCORLIB/Platform::String::Begin
- VCCORLIB/Platform::String::CompareOrdinal
- VCCORLIB/Platform::String::Concat
- VCCORLIB/Platform::String::Data
- VCCORLIB/Platform::String::Dispose
- VCCORLIB/Platform::String::End
- VCCORLIB/Platform::String::Equals
- VCCORLIB/Platform::String::GetHashCode
- VCCORLIB/Platform::String::IsEmpty
- VCCORLIB/Platform::String::IsFastPass
- VCCORLIB/Platform::String::Length
- VCCORLIB/Platform::String::ToString
dev_langs:
- C++
helpviewer_keywords:
- Platform::String
ms.assetid: 72dd04a4-a694-40d3-b899-eaa0b503eab8
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3c665b6767ea7a7a7d97d232f5253f8e182e6b0a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="platformstring-class"></a>Klasa platform::String
Reprezentuje kolekcję sekwencyjnych znaków Unicode, który jest używany do reprezentowania tekstu. Aby uzyskać dodatkowe informacje i przykłady, zobacz [ciągów](../cppcx/strings-c-cx.md).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
  
public ref class String sealed : Object,  
    IDisposable,  
    IEquatable,  
    IPrintable  
```  
  
## <a name="iterators"></a>Iteratory  
 Dwie funkcje iteracyjne, które nie są członkami klasy String, może być używany z `std::for_each` funkcji szablonu wyliczyć znaków w obiekcie String.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`const char16* begin(String^ s)`|Zwraca wskaźnik do początku określonego obiektu na ciąg.|  
|`const char16* end(String^ s)`|Zwraca wskaźnik poza końcem ciągu określonego obiektu.|  
  
### <a name="members"></a>Elementy członkowskie  
 Klasa ciąg dziedziczy obiektu i interfejsów interfejs IDisposable, interfejsu IEquatable i IPrintable.  
  
 Klasa ciąg ma również następujące typy elementów członkowskich.  
  
 **Konstruktory**  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|[String::String](#ctor)|Inicjuje nowe wystąpienie klasy String.|  
  
 **Metody**  
  
 Klasa ciąg dziedziczy z metody metodę Equals, Finalize() metoda GetHashCode(), GetType(), MemberwiseClose() i ToString() [Platform::Object klasy](../cppcx/platform-object-class.md). Ciąg zawiera również następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[String::Begin](#begin)|Zwraca wskaźnik do początku bieżącego ciągu.|  
|[String::CompareOrdinal](#compareordinal)|Porównuje dwa `String` obiektów w wyniku obliczenia wartości liczbowe odpowiadające im znaki w ciągu dwóch wartości reprezentowane przez obiekty.|  
|[String::concat](#concat)|Łączy dwa obiekty ciągu wartości.|  
|[String::Data](#data)|Zwraca wskaźnik do początku bieżącego ciągu.|  
|[String::Dispose](#dispose)|Zwalnia lub zwalnia zasoby.|  
|[String::end](#end)|Zwraca wskaźnik poza koniec bieżących parametrów.|  
|[String::Equals](#equals)|Wskazuje, czy określony obiekt jest taki sam jak bieżący obiekt.|  
|[String::GetHashCode](#gethashcode)|Zwraca kod skrótu dla tego wystąpienia.|  
|[String::IsEmpty](#isempty)|Wskazuje, czy bieżący obiekt ciąg jest pusty.|  
|[String::IsFastPass](#isfastpass)|Wskazuje, czy bieżący obiekt jest ciąg uczestniczy w *szybko przekazywany* operacji. Szybkie dokonują operacji, liczenie odwołań jest wstrzymana.|  
|[String::Length](#length)|Pobiera długość ciągu bieżącego obiektu.|  
|[String::ToString](#tostring)|Zwraca obiekt ciągu, którego wartość jest taka sama jak bieżący ciąg.|  
  
 **Operatory**  
  
 Klasa ciąg ma następujące operatory.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|[String::operator == — Operator](#operator-equality)|Wskazuje, czy dwa obiekty ciągu określonego mają taką samą wartość.|  
|[operator + — Operator](#operator-plus)|Łączy dwa obiekty ciąg do nowego obiektu ciąg.|  
|[String::operator > — Operator](#operator-greater-than)|Wskazuje, czy wartość jednego ciągu obiektu jest większa niż wartość drugiej obiektem ciągu.|  
|[String::operator > = — Operator](#operator-greater-than-or-equals)|Wskazuje, czy wartość jednego ciągu obiektu jest większa lub równa wartości drugi obiekt String.|  
|[String::operator! = — Operator](#operator-inequality)|Wskazuje, czy dwa obiekty ciągu określonego mają różne wartości.|  
|[String::operator < — Operator](#operator-less-than)|Wskazuje, czy wartość jednego ciągu obiektu jest mniejsza niż wartość drugiej obiektem ciągu.|  
  
### <a name="requirements"></a>Wymagania  
 **Minimalna obsługiwana klienta:** systemu Windows 8  
  
 **Minimalna obsługiwana serwera:** systemu Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Nagłówek** vccorlib.h (domyślnie włączone)  

 
## <a name="begin"></a>  String::BEGIN — metoda
Zwraca wskaźnik do początku bieżącego ciągu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
  
char16* Begin()  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do początku bieżącego ciągu.  
  
## <a name="compareordinal"></a>  String::CompareOrdinal — metoda
Porównuje dwa `String` obiektów w wyniku obliczenia wartości liczbowe odpowiadające im znaki w ciągu dwóch wartości reprezentowane przez obiekty.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
  
int CompareOrdinal(  
           String^ str1,   
           String^ str2)  
  
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 Pierwszy ciąg obiektu.  
  
 `str2`  
 Drugi obiekt String.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba całkowita, która wskazuje leksykalne relację między dwiema comparands. W poniższej tabeli przedstawiono możliwe wartości zwracane.  
  
|Wartość|Warunek|  
|-----------|---------------|  
|-1|`str1` jest mniejsza niż `str2`.|  
|0|`str1` jest to `str2`.|  
|1|`str1` jest większa niż `str2`.|  
  


## <a name="concat"></a>  String::concat — metoda
Łączy dwa obiekty ciągu wartości.  
  
### <a name="syntax"></a>Składnia  
  
```cpp    
String^ Concat( String^ str1, String^ str2)  
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 Pierwszy ciąg obiekt, lub `null`.  
  
 `str2`  
 Drugi obiekt String lub `null`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Nowe parametry ^ obiektu, którego wartość jest połączenie wartości występujących z `str1` i `str2`.  
  
 Jeśli `str1` jest `null` i `str2` nie jest `str1` jest zwracany. Jeśli `str2` jest `null` i `str1` nie jest `str2` jest zwracany. Jeśli `str1` i `str2` są `null`, ciąg pusty (L"") jest zwracany.  
  


## <a name="data"></a>  String::Data — metoda
Zwraca wskaźnik do początku buforu danych obiektu jako tablica stylu języka C `char16` (`wchar_t`) elementów.  
  
### <a name="syntax"></a>Składnia  
  
```  
const char16* Data()  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do początku `const char16` tablicy znaków Unicode (`char16` jest elementem typedef dla `wchar_t`).  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia przekonwertowanie z `Platform::String^` do `wchar_t*`. Gdy `String` obiektu wykracza poza zakres, wskaźnika danych nie jest gwarantowana jest nieprawidłowy. Do przechowywania danych poza okres istnienia oryginalnej `String` obiektów, użyj [wcscpy_s —](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) do kopiowania tablicy do pamięci, że przydzielił samodzielnie.  
  


## <a name="dispose"></a>  String::Dispose — metoda
Zwalnia lub zwalnia zasoby.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
  
virtual override void Dispose()  
```  

## <a name="end"></a>  String::end — metoda
Zwraca wskaźnik poza koniec bieżących parametrów.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
  
char16* End()  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do poza koniec bieżących parametrów.  
  
### <a name="remarks"></a>Uwagi  
 END() zwraca Begin() i długości.  
  


## <a name="equals"></a>  String::Equals — metoda
Wskazuje, czy podany ciąg ma taką samą wartość jak bieżący obiekt.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
  
bool String::Equals(Object^ str);  
  
bool String::Equals(String^ str);  
  
```  
  
### <a name="parameters"></a>Parametry  
 `str`  
 Obiekt do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli `str` jest taki sam jak bieżący obiekt, a w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest odpowiednikiem [String::CompareOrdinal](#compareordinal). W pierwszym przeciążenia oczekuje `str` parametru mogą być rzutowane na ciąg ^ obiektu.  
  


## <a name="gethashcode"></a>  String::GetHashCode — metoda
Zwraca kod skrótu dla tego wystąpienia.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
  
virtual override int GetHashCode()  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Kod skrótu dla tego wystąpienia.  
  


## <a name="isempty"></a>  String::IsEmpty — metoda
Wskazuje, czy bieżący obiekt ciąg jest pusty.  
  
### <a name="syntax"></a>Składnia  
  
```cpp    
bool IsEmpty()  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli bieżący obiekt ciągu jest `null` lub ciąg pusty (L""); w przeciwnym razie `false`.  
  


## <a name="isfastpass"></a>  String::IsFastPass — metoda
Wskazuje, czy bieżący obiekt jest ciąg uczestniczy w *szybko przekazywany* operacji. Szybkie dokonują operacji, liczenie odwołań jest wstrzymana.  
  
### <a name="syntax"></a>Składnia  
  
```cpp    
bool IsFastPass();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli bieżący obiekt ciągu jest przeszłości fast; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 W wywołaniu funkcji, której obiekt zliczane odwołania jest parametrem i wywołana funkcja odczytuje tylko ten obiekt kompilator można bezpiecznie zawiesić liczenie odwołań w i poprawianie wydajności wywołania. Nie ma nic przydatne, że kod można wykonać za pomocą tej właściwości. System obsługuje wszystkie szczegóły.  
  


## <a name="length"></a>  String::length — metoda
Pobiera liczbę znaków w ciągu bieżącego obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp    
unsigned int Length()  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba znaków w ciągu bieżącego obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Długość ciągu bez znaków wynosi zero. Długość ciągu następujące wynosi 5:  
  
```    
String^ str = "Hello";  
int len = str->Length(); //len = 5  
```  
  
 Tablica znaków zwrócona przez [String::Data](#data) ma jeden znak dodatkowe zakończenia wartość NULL lub '\0'. Ten znak jest również dwa bajty.  
  


## <a name="operator-plus"></a>  String::operator + — Operator
Łączy dwa [ciąg](../cppcx/platform-string-class.md) obiektów w nowym [ciąg](../cppcx/platform-string-class.md) obiektu.
  
### <a name="syntax"></a>Składnia  
  
```cpp  
  
bool String::operator+( String^ str1, String^ str2)  
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 Pierwszy `String` obiektu.  
  
 `str2`  
 Drugi `String` obiektu, którego zawartość zostanie dołączona do `str1`.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli `str1` jest równa `str2`; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Ten operator tworzy `String^` obiekt, który zawiera dane z dwóch argumentów operacji. Użyć go jako udogodnienie najwyższej wydajności nie jest krytyczna. Kilka wywołania "`+`" w funkcji prawdopodobnie nie będą widoczne, ale jeśli modyfikujesz dużych obiektów lub dane tekstowe w pętli ścisłej Użyj standard C++ mechanizmów i typów.  
  
##  <a name="operator-equality"></a> String::operator == — Operator
Wskazuje, czy dwa obiekty określonego ciągu mieć taką samą wartość tekstu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp    
bool String::operator==( String^ str1, String^ str2)  
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 Pierwszy ciąg obiekt do porównania.  
  
 `str2`  
 Drugi ciąg obiekt do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli zawartość `str1` są równe `str2`; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Ten operator jest odpowiednikiem [String::CompareOrdinal](#compareordinal).  
  


##  <a name="operator-greater-than"></a>  String::operator&gt; 
Wskazuje, czy wartość jednego ciągu obiektu jest większa niż wartość drugiej obiektem ciągu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp    
bool String::operator>( String^ str1, String^ str2)  
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 Pierwszy ciąg obiektu.  
  
 `str2`  
 Drugi obiekt String.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli wartość `str1` jest większa niż wartość `str2`; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Ten operator jest odpowiednikiem jawnie podczas wywoływania [String::CompareOrdinal](#compareordinal) i pobierania wynik jest większa od zera.  
  


## <a name="operator-greater-than-or-equals"></a> String::operator&gt;= 
Wskazuje, czy wartość jednego ciągu obiektu jest większa lub równa wartości drugi obiekt String.  
  
### <a name="syntax"></a>Składnia  
  
```cpp    
bool String::operator>=( String^ str1, String^ str2) 
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 Pierwszy ciąg obiektu.  
  
 `str2`  
 Drugi obiekt String.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli wartość `str1` jest większa lub równa wartości `str2`; w przeciwnym razie `false`.  
  


## <a name="operator-inequality"></a> String::operator! = 
Wskazuje, czy dwa obiekty ciągu określonego mają różne wartości.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
bool String::operator!=( String^ str1, String^ str2)  
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 Pierwszy ciąg obiekt do porównania.  
  
 `str2`  
 Drugi ciąg obiekt do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli `str1` nie jest równa `str2`; w przeciwnym razie `false`.   


## <a name="operator-less-than"></a> String::operator&lt; 
Wskazuje, czy wartość jednego ciągu obiektu jest mniejsza niż wartość drugiej obiektem ciągu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
bool String::operator<( String^ str1, String^ str2)  
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 Pierwszy ciąg obiektu.  
  
 `str2`  
 Drugi obiekt String.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli wartość `str1` jest mniejsza niż wartość `str2`; w przeciwnym razie `false`.  
  
## <a name="ctor"></a> Konstruktor String::String
Inicjuje nowe wystąpienie klasy String kopię danych ciągu wejściowego.  
  
### <a name="syntax"></a>Składnia  
  
```cpp    
String();    
String(char16* s)  
String(char16* s, unsigned int n)  
```  
  
### <a name="parameters"></a>Parametry  
 `s`  
 Seria znaki dwubajtowe, które inicjuje ciąg. char16  
  
 `n`  
 Liczba określająca długość ciągu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ma kluczowe znaczenie i zarządzają okresem istnienia ciągu źródła, możesz użyć [Platform::StringReference](../cppcx/platform-stringreference-class.md) zamiast ciągu.  
### <a name="example"></a>Przykład  
  
```cpp  
String^ s = L"Hello!";  
```  
  
## <a name="tostring"></a> String::toString
Zwraca obiekt ciągu, którego wartość jest taka sama jak bieżący ciąg.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
String^ String::ToString()  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Obiekt ciągu, którego wartość jest taka sama jak bieżący ciąg.  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)