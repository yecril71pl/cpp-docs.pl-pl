---
title: "strstreambuf — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- strstream/std::strstreambuf::freeze
- strstream/std::strstreambuf::overflow
- strstream/std::strstreambuf::pbackfail
- strstream/std::strstreambuf::pcount
- strstream/std::strstreambuf::seekoff
- strstream/std::strstreambuf::seekpos
- strstream/std::strstreambuf::str
- strstream/std::strstreambuf::underflow
dev_langs: C++
helpviewer_keywords:
- std::strstreambuf [C++], freeze
- std::strstreambuf [C++], overflow
- std::strstreambuf [C++], pbackfail
- std::strstreambuf [C++], pcount
- std::strstreambuf [C++], seekoff
- std::strstreambuf [C++], seekpos
- std::strstreambuf [C++], str
- std::strstreambuf [C++], underflow
ms.assetid: b040b8ea-0669-4eba-8908-6a9cc159c54b
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cb7d7c601ab2750e01202bba7dbefcb05673a025
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="strstreambuf-class"></a>strstreambuf — Klasa
W tym artykule opisano buforu strumienia, który kontroluje przesyłania elementów do i z sekwencję elementy przechowywane w `char` tablicy obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```  
class strstreambuf : public streambuf  
```  
  
## <a name="remarks"></a>Uwagi  
 W zależności od sposobu konstruowania obiektu go można być przydzielone, rozszerzony i zwolniony w razie potrzeby w celu uwzględnienia zmian w sekwencji.  
  
 Obiekt klasy `strstreambuf` przechowuje kilka bity informacji o trybie jako jego `strstreambuf` tryb. Bity te wskazują czy kontrolowanej sekwencji:  
  
-   Została przydzielona i musi zostać zwolniony po pewnym czasie.  
  
-   Jest można modyfikować.  
  
-   To rozszerzalna przez ponowne przydzielanie magazynu.  
  
-   Została zablokowana i dlatego musi być odblokowany przed zniszczone obiekt lub zwolniony (Jeśli przydzielone) Agencja niż obiekt.  
  
 Kontrolowanej sekwencji, który jest zablokowana nie można zmodyfikować lub extended, bez względu na stan tych bitów trybu osobnych.  
  
 Obiekt przechowuje także wskaźniki do dwóch funkcji, które kontrolują `strstreambuf` alokacji. Jeśli są one wskaźniki o wartości null, obiekt devises własną metodę alokacji i zwalnianie magazynu w kontrolowanej sekwencji.  
  
> [!NOTE]
>  Ta klasa jest przestarzały. Należy rozważyć użycie [stringbuf](../standard-library/sstream-typedefs.md#stringbuf) lub [wstringbuf](../standard-library/sstream-typedefs.md#wstringbuf) zamiast tego.  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[strstreambuf —](#strstreambuf)|Tworzy obiekt typu `strstreambuf`.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[blokowanie](#freeze)|Powoduje, że jest niedostępna za pośrednictwem operacji buforu strumienia buforu strumienia.|  
|[przepełnienie](#overflow)|Chronione funkcji wirtualnej można wywołać po wstawieniu nowego znaku w buforze pełna.|  
|[pbackfail](#pbackfail)|Chroniony element członkowski wirtualnego funkcję, która próbuje zawiesić elementu z powrotem do strumienia wejściowego, a następnie dokonaj jego bieżącego elementu (wskazywana przez wskaźnik następnej).|  
|[pcount](#pcount)|Zwraca liczbę z liczbą elementów zapisywane w kontrolowanej sekwencji.|  
|[seekoff](#seekoff)|Funkcja chroniony element członkowski wirtualnego próbuje zmienić bieżącego położenia dla strumieni kontrolowane.|  
|[seekpos](#seekpos)|Funkcja chroniony element członkowski wirtualnego próbuje zmienić bieżącego położenia dla strumieni kontrolowane.|  
|[str](#str)|Wywołania [Zablokuj](#freeze), a następnie zwraca wskaźnik do początku kontrolowanej sekwencji.|  
|[niedopełnienie](#underflow)|Chroniony funkcją wirtualną można wyodrębnić bieżącego elementu ze strumienia wejściowego.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<strstream — >  
  
 **Namespace:** Standard  
  
##  <a name="freeze"></a>strstreambuf::FREEZE  
 Powoduje, że jest niedostępna za pośrednictwem operacji buforu strumienia buforu strumienia.  
  
```  
void freeze(bool _Freezeit = true);
```  
  
### <a name="parameters"></a>Parametry  
 `_Freezeit`  
 A `bool` wskazującą, czy ma strumień jest zablokowana.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `_Freezeit` ma wartość true, funkcja zmienia zapisana `strstreambuf` tryb dokonanie kontrolowanej sekwencji zablokowane. W przeciwnym razie ułatwia kontrolowanej sekwencji nie są zablokowane.  
  
 [str](#str) oznacza `freeze`.  
  
> [!NOTE]
>  Zablokowane buforu nie zostanie zwolniona podczas `strstreambuf` zniszczenia. Rozmiar buforu musi Odblokuj, zanim zostanie zwolniona w celu uniknięcia wycieku pamięci.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// strstreambuf_freeze.cpp  
// compile with: /EHsc  
  
#include <iostream>  
#include <strstream>  
  
using namespace std;  
  
void report(strstream &x)  
{  
    if (!x.good())  
        cout << "stream bad" << endl;  
    else  
        cout << "stream good" << endl;  
}  
  
int main()  
{  
    strstream x;  
  
    x << "test1";  
    cout << "before freeze: ";  
    report(x);  
  
    // Calling str freezes stream.  
    cout.write(x.rdbuf()->str(), 5) << endl;  
    cout << "after freeze: ";  
    report(x);  
  
    // Stream is bad now, wrote on frozen stream  
    x << "test1.5";  
    cout << "after write to frozen stream: ";  
    report(x);  
  
    // Unfreeze stream, but it is still bad  
    x.rdbuf()->freeze(false);  
    cout << "after unfreezing stream: ";  
    report(x);  
  
    // Clear stream  
    x.clear();  
    cout << "after clearing stream: ";  
    report(x);  
  
    x << "test3";  
    cout.write(x.rdbuf()->str(), 10) << endl;  
  
    // Clean up.  Failure to unfreeze stream will cause a  
    // memory leak.  
    x.rdbuf()->freeze(false);  
}  
```  
  
```Output  
before freeze: stream good  
test1  
after freeze: stream good  
after write to frozen stream: stream bad  
after unfreezing stream: stream bad  
after clearing stream: stream good  
test1test3  
```  
  
##  <a name="overflow"></a>strstreambuf::Overflow  
 Chronione funkcji wirtualnej można wywołać po wstawieniu nowego znaku w buforze pełna.  
  
```  
virtual int overflow(int _Meta = EOF);
```  
  
### <a name="parameters"></a>Parametry  
 `_Meta`  
 Znak do wstawienia w buforze, lub `EOF`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja nie może się powieść, zwraca `EOF`. W przeciwnym razie, jeśli _ *Meta* == `EOF`, zwraca niektóre wartości innych niż `EOF`. W przeciwnym razie zwraca \_ *Meta*.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli _ *Meta* ! = `EOF`, funkcja chroniony element członkowski wirtualnego próbuje wstawić elementu ( `char`)\_ *Meta* w buforze danych wyjściowych. Go to zrobić na różne sposoby:  
  
-   Jeśli pozycja zapisu jest dostępny, można przechowywać elementu w miejscu zapisu i zwiększyć wskaźnik następnej buforu danych wyjściowych.  
  
-   Jeśli tryb przechowywanych strstreambuf — stwierdzający, że jest kontrolowanej sekwencji można modyfikować, rozszerzalne i nie jest zablokowane, funkcja można udostępnić pozycję zapisu przydzielając nowych buforu danych wyjściowych. Rozszerzanie buforu wyjściowego w ten sposób rozszerzają wszystkie skojarzone buforu wejściowego.  
  
##  <a name="pbackfail"></a>strstreambuf::pbackfail  
 Funkcja chronionego członka wirtualnego, który próbuje ponownie poddane elementu wejściowego strumienia, a następnie ułatwia bieżącego elementu (wskazywana przez wskaźnik następnej).  
  
```  
virtual int pbackfail(int _Meta = EOF);
```  
  
### <a name="parameters"></a>Parametry  
 `_Meta`  
 Znak do wstawienia w buforze, lub `EOF`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja nie może się powieść, zwraca `EOF`. W przeciwnym razie, jeśli _ *Meta* == `EOF`, zwraca niektóre wartości innych niż `EOF`. W przeciwnym razie zwraca \_ *Meta*.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja chroniony element członkowski wirtualnego próbuje ponownie poddane element buforze wejściowym, a następnie wprowadź go bieżącego elementu (wskazywana przez wskaźnik następnej).  
  
 Jeśli _ *Meta* == `EOF`, elementu do usunięcia jest już w strumieniu przed bieżącego elementu. W przeciwnym razie ten element został zastąpiony przez **ch** = ( `char`)\_ *Meta*. Funkcja można odłożyć element na różne sposoby:  
  
-   Jeśli pozycja putback jest dostępne, a element przechowywane porównuje równa **ch**, jego zmniejszanie wskaźnik następnej dla buforu wejściowego.  
  
-   Jeśli pozycja putback jest dostępne, a jeśli tryb strstreambuf — kontrolowanej sekwencji jest można modyfikować, funkcja może przechowywać **ch** w pozycji putback i dekrementacja wskaźnik następnej dla buforu wejściowego.  
  
##  <a name="pcount"></a>strstreambuf::pcount  
 Zwraca liczbę z liczbą elementów zapisywane w kontrolowanej sekwencji.  
  
```  
streamsize pcount() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów zapisywane w kontrolowanej sekwencji.  
  
### <a name="remarks"></a>Uwagi  
 W szczególności jeśli [pptr](../standard-library/basic-streambuf-class.md#pptr) jest wskaźnika o wartości null, funkcja zwraca wartość zero. W przeciwnym razie zwraca `pptr`  -  [pbase](../standard-library/basic-streambuf-class.md#pbase).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// strstreambuf_pcount.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <strstream>  
using namespace std;  
  
int main( )  
{  
   strstream x;  
   x << "test1";  
   cout << x.rdbuf( )->pcount( ) << endl;  
   x << "test2";  
   cout << x.rdbuf( )->pcount( ) << endl;  
}  
```  
  
##  <a name="seekoff"></a>strstreambuf::seekoff  
 Funkcja chroniony element członkowski wirtualnego próbuje zmienić bieżącego położenia dla strumieni kontrolowane.  
  
```  
virtual streampos seekoff(streamoff _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```  
  
### <a name="parameters"></a>Parametry  
 `_Off`  
 Położenie do wyszukania dla względem `_Way`.  
  
 `_Way`  
 Punkt początkowy dla operacji przesunięcia. Zobacz [seekdir](../standard-library/ios-base-class.md#seekdir) prawidłowych wartości.  
  
 `_Which`  
 Określa tryb pozycję wskaźnika. Wartość domyślna to umożliwia modyfikowanie, Odczyt i zapis pozycji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Funkcja powiedzie się w jednej zmiany lub strumienia obie pozycje, zwraca pozycji w strumieniu wynikowe. W przeciwnym razie nie powiedzie się i zwraca pozycję nieprawidłowy strumień.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja chroniony element członkowski wirtualnego usiłują alter dla strumieni kontrolowane bieżącej pozycji. W przypadku obiektu strstreambuf — klasa pozycji w strumieniu składa się wyłącznie z przesunięciu strumienia. Przesunięcia zero oznacza pierwszy element kontrolowanej sekwencji.  
  
 Nowa pozycja jest określane w następujący sposób:  
  
-   Jeśli `_Way`  ==  `ios_base::beg`, nowe położenie jest na początku strumienia plus _ *poza*.  
  
-   Jeśli `_Way`  ==  `ios_base::cur`, nowe położenie jest bieżącej pozycji strumienia plus _ *poza*.  
  
-   Jeśli `_Way`  ==  `ios_base::end`, nowe położenie jest koniec strumienia plus _ *poza*.  
  
 Jeśli `_Which`  &  **ios_base::in** jest różna od zera i istnieje buforu wejściowego, funkcja zmienia pozycję dalej do odczytu w buforze wejściowym. Jeśli `_Which`  &  **ios_base::out** również jest różna od zera, `_Way` ! = **ios_base::cur**i istnieje buforu wyjściowego, funkcja ustawia również dalej pozycji do zapisania do dopasowania Pozycja dalej do odczytu.  
  
 W przeciwnym razie, jeśli `_Which`  &  `ios_base::out` jest różna od zera i istnieje buforu wyjściowego, funkcja zmienia dalej pozycji do zapisania w buforze danych wyjściowych. W przeciwnym razie pozycjonowania kończy się niepowodzeniem. Pozycjonowania operacja się powiodła wynikowy pozycji strumienia musi znajdować się w kontrolowanej sekwencji.  
  
##  <a name="seekpos"></a>strstreambuf::seekpos  
 Funkcja chroniony element członkowski wirtualnego próbuje zmienić bieżącego położenia dla strumieni kontrolowane.  
  
```  
virtual streampos seekpos(streampos _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```  
  
### <a name="parameters"></a>Parametry  
 `_Sp`  
 Położenie do wyszukania dla.  
  
 `_Which`  
 Określa tryb pozycję wskaźnika. Wartość domyślna to umożliwia modyfikowanie, Odczyt i zapis pozycji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Funkcja powiedzie się w jednej zmiany lub strumienia obie pozycje, zwraca pozycji w strumieniu wynikowe. W przeciwnym razie nie powiedzie się i zwraca pozycję nieprawidłowy strumień. Aby ustalić, czy pozycja strumienia jest nieprawidłowa, porównanie wartości zwracanych z `pos_type(off_type(-1))`.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja chroniony element członkowski wirtualnego usiłują alter dla strumieni kontrolowane bieżącej pozycji. W przypadku obiektu strstreambuf — klasa pozycji w strumieniu składa się wyłącznie z przesunięciu strumienia. Przesunięcia zero oznacza pierwszy element kontrolowanej sekwencji. Nowa pozycja jest określany przez _ *Sp*.  
  
 Jeśli `_Which`  &  **ios_base::in** jest różna od zera i istnieje buforu wejściowego, funkcja zmienia pozycję dalej do odczytu w buforze wejściowym. Jeśli `_Which`  &  `ios_base::out` jest różna od zera i istnieje buforu wyjściowego, funkcja ustawia również dalej pozycji do zapisania do dopasowania dalej pozycji do odczytu. W przeciwnym razie, jeśli `_Which`  &  `ios_base::out` jest różna od zera i istnieje buforu wyjściowego, funkcja zmienia dalej pozycji do zapisania w buforze danych wyjściowych. W przeciwnym razie pozycjonowania kończy się niepowodzeniem. Pozycjonowania operacja się powiodła wynikowy pozycji strumienia musi znajdować się w kontrolowanej sekwencji.  
  
##  <a name="str"></a>strstreambuf::str  
 Wywołania [Zablokuj](#freeze), a następnie zwraca wskaźnik do początku kontrolowanej sekwencji.  
  
```  
char *str();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do początku kontrolowanej sekwencji.  
  
### <a name="remarks"></a>Uwagi  
 Element o wartości null nie przerywania istnieje, chyba że użytkownik jawnie Włóż dysk.  
  
### <a name="example"></a>Przykład  
  Zobacz [strstreambuf::freeze](#freeze) dla przykładu korzystającego z **str**.  
  
##  <a name="strstreambuf"></a>strstreambuf::strstreambuf  
 Tworzy obiekt typu `strstreambuf`.  
  
```  
explicit strstreambuf(streamsize count = 0);

strstreambuf(void (* _Allocfunc)(size_t),
    void (* _Freefunc)(void*));

strstreambuf(char* _Getptr,
    streamsize count,
    char* _Putptr = 0);

strstreambuf(signed char* _Getptr,
    streamsize count,
    signed char* _Putptr = 0);

strstreambuf(unsigned char* _Getptr,
    streamsize count,
    unsigned char* _Putptr = 0);

strstreambuf(const char* _Getptr,
    streamsize count);

strstreambuf(const signed char* _Getptr,
    streamsize count);

strstreambuf(const unsigned char* _Getptr,
    streamsize count);
```  
  
### <a name="parameters"></a>Parametry  
 *_Allocfunc*  
 Funkcja używana można przydzielić bufora pamięci.  
  
 `count`  
 Określa długość buforu wskazywana przez `_Getptr`. Jeśli `_Getptr` nie jest argumentem (forma konstruktora pierwszy), alokacji sugerowany rozmiar buforów.  
  
 *_Freefunc*  
 Funkcja używana do wolnego buforu pamięci.  
  
 `_Getptr`  
 Bufor używany dla danych wejściowych.  
  
 `_Putptr`  
 Bufor używany dla danych wyjściowych.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy Konstruktor przechowuje wskaźnika o wartości null w wszystkie wskaźniki kontrolowanie buforu wejściowego, buforu wyjściowego i strstreambuf — alokacji. Ustawia tryb przechowywanych strstreambuf — aby kontrolowanej sekwencji można modyfikować i rozszerzalna. Również akceptuje `count` jako sugerowane początkowy rozmiar alokacji.  
  
 Drugi Konstruktor zachowuje się jak pierwszy, z wyjątkiem tego, że przechowuje _ *Allocfunc* jako wskaźnik do funkcji do wywołania, aby przydzielić magazyn i \_ *Freefunc* jako wskaźnik do funkcji Wywołanie zwolnienia tego magazynu.  
  
 Konstruktory trzy:  
  
```  
strstreambuf(char *_Getptr,
    streamsize count,  
    char *putptr = 0);
  
strstreambuf(signed char *_Getptr,
    streamsize count,  
    signed char *putptr = 0);
  
strstreambuf(unsigned char *_Getptr,
    streamsize count,  
    unsigned char *putptr = 0);
```  
  
 również przypominają pierwsza strona, z wyjątkiem `_Getptr` określa obiekt array używanym do przechowywania kontrolowanej sekwencji. (W związku z tym nie może być wskaźnika o wartości null.) Liczba elementów *N* w tablicy jest określane w następujący sposób:  
  
-   Jeśli (`count` > 0), następnie *N* jest `count`.  
  
-   Jeśli (`count` == 0), następnie *N* jest `strlen`(( **const** `char` *) `_Getptr` ).  
  
-   Jeśli (`count` < 0), następnie *N* jest **int_max —**.  
  
 Jeśli `_Putptr` jest wskaźnika o wartości null, funkcja ustanawia tylko buforu wejściowego, wykonując:  
  
```  
setg(_Getptr,
    _Getptr,
    _Getptr + N);
```  
  
 W przeciwnym razie ustanawia wejścia i wyjścia buforów, wykonując:  
  
```  
setg(_Getptr,
    _Getptr,
    _Putptr);

setp(_Putptr,
    _Getptr + N);
```  
  
 W takim przypadku `_Putptr` musi być w interwale [ `_Getptr`, `_Getptr`  +  *N*].  
  
 Na koniec trzy konstruktory:  
  
```  
strstreambuf(const char *_Getptr,
    streamsize count);

strstreambuf(const signed char *_Getptr,
    streamsize count);

strstreambuf(const unsigned char *_Getptr,
    streamsize count);
```  
  
 wszystkie działają tak samo, jak:  
  
```  
streambuf((char *)_Getptr, count);
```  
  
 z tą różnicą, że przechowywanej tryb sprawia, że kontrolowanej sekwencji można modyfikować ani rozszerzalne.  
  
##  <a name="underflow"></a>strstreambuf::underflow  
 Chroniony funkcją wirtualną można wyodrębnić bieżącego elementu ze strumienia wejściowego.  
  
```  
virtual int underflow();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja nie może się powieść, zwraca `EOF`. W przeciwnym razie zwraca bieżący element w strumieniu wejściowym przekonwertować zgodnie z powyższym opisem.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja chroniony element członkowski wirtualnego usiłują wyodrębnić bieżącego elementu **ch** z buforu wejściowego, następnie poprawić bieżącej pozycji strumienia i zwracać element jako (`int`) (`unsigned char`) **ch** . Go to zrobić w tylko jednym ze sposobów: Jeśli pozycja odczytu jest dostępny, przyjmuje **ch** jako element przechowywane w pozycji odczytu i przesuwa wskaźnik następnej dla buforu wejściowego.  
  
## <a name="see-also"></a>Zobacz też  
 [streambuf](../standard-library/streambuf-typedefs.md#streambuf)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream — programowanie](../standard-library/iostream-programming.md)   
 [Konwencje iostream](../standard-library/iostreams-conventions.md)

