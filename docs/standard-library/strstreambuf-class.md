---
title: strstreambuf — Klasa
ms.date: 11/04/2016
f1_keywords:
- strstream/std::strstreambuf::freeze
- strstream/std::strstreambuf::overflow
- strstream/std::strstreambuf::pbackfail
- strstream/std::strstreambuf::pcount
- strstream/std::strstreambuf::seekoff
- strstream/std::strstreambuf::seekpos
- strstream/std::strstreambuf::str
- strstream/std::strstreambuf::underflow
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
ms.openlocfilehash: 75c9a96b727ef60280055536296f850f492d16ac
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327307"
---
# <a name="strstreambuf-class"></a>strstreambuf — Klasa

W tym artykule opisano buforu strumieni, który kontroluje przekazywanie elementów do i z sekwencji elementów przechowywanych w **char** obiektu array.

## <a name="syntax"></a>Składnia

```cpp
class strstreambuf : public streambuf
```

## <a name="remarks"></a>Uwagi

W zależności od tego, jak obiekt jest konstruowany jego może można przydzielone, rozszerzać, a zwolniona zgodnie z potrzebami, aby uwzględnić zmiany w sekwencji.

Obiekt klasy `strstreambuf` przechowuje kilka bitów informacji o trybie jako jego `strstreambuf` trybu. Te bity wskazują czy kontrolowanej sekwencji:

- Została przydzielona i musi być zwolniona po pewnym czasie.

- To można modyfikować.

- Jest rozszerzalnej ponowne przydzielanie magazynu.

- Został zamrożony i dlatego musi być są przed obiekt jest niszczony lub zwolnione (jeśli jest przydzielona) przez agencję innego niż obiekt.

Kontrolowanej sekwencji, która jest zamrożony nie można zmodyfikować lub przedłużony, bez względu na stan tych bitów trybu osobnych.

Obiekt przechowuje również wskaźniki do dwóch funkcji, które kontrolują `strstreambuf` alokacji. Jeśli są one wskaźników o wartości null, obiekt devises własną metodę przydzielanie i zwalnianie pamięci masowej dla kontrolowanej sekwencji.

> [!NOTE]
> Ta klasa jest przestarzały. Należy rozważyć użycie [stringbuf](../standard-library/sstream-typedefs.md#stringbuf) lub [wstringbuf](../standard-library/sstream-typedefs.md#wstringbuf) zamiast tego.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[strstreambuf](#strstreambuf)|Tworzy obiekt typu `strstreambuf`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[blokowanie](#freeze)|Powoduje, że bufor strumienia będzie dostępny za pośrednictwem operacji buforu strumienia.|
|[overflow](#overflow)|Chronione funkcja wirtualna, która może być wywoływana po wstawieniu do buforu pełnej nowego znaku.|
|[pbackfail](#pbackfail)|Funkcja chronionych wirtualna elementu członkowskiego, która próbuje umieścić element z powrotem do strumienia wejściowego i przypisz ją po bieżącego elementu (wskazywany przez wskaźnik następnej).|
|[pcount —](#pcount)|Zwraca liczbę elementów zapisywane w kontrolowanej sekwencji.|
|[seekoff](#seekoff)|Funkcja chronionych wirtualna elementu członkowskiego, która próbuje zmienić dla strumieni kontrolowanego bieżącej pozycji.|
|[seekpos —](#seekpos)|Funkcja chronionych wirtualna elementu członkowskiego, która próbuje zmienić dla strumieni kontrolowanego bieżącej pozycji.|
|[str](#str)|Wywołania [freeze](#freeze), a następnie zwraca wskaźnik do początku kontrolowanej sekwencji.|
|[underflow](#underflow)|Chroniony funkcją wirtualną można wyodrębnić bieżącego elementu ze strumienia wejściowego.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<strstream — >

**Namespace:** standardowe

## <a name="freeze"></a>  strstreambuf::FREEZE

Powoduje, że bufor strumienia będzie dostępny za pośrednictwem operacji buforu strumienia.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Parametry

*_Freezeit*<br/>
A **bool** wskazującą, czy chcesz, aby strumień jest zablokowana.

### <a name="remarks"></a>Uwagi

Jeśli *_Freezeit* ma wartość true, funkcja zmienia przechowywaną `strstreambuf` tryb się kontrolowanej sekwencji, zamrożone. W przeciwnym razie ułatwia kontrolowanej sekwencji, które nie są zablokowane.

[str](#str) oznacza `freeze`.

> [!NOTE]
> Zamrożone buforu nie zostanie zwolniona podczas `strstreambuf` zniszczenia. Rozmiar buforu musi Odblokuj, zanim zostanie zwolniony w celu uniknięcia wycieku pamięci.

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

## <a name="overflow"></a>  strstreambuf::Overflow

Chronione funkcja wirtualna, która może być wywoływana po wstawieniu do buforu pełnej nowego znaku.

```cpp
virtual int overflow(int _Meta = EOF);
```

### <a name="parameters"></a>Parametry

*_Meta*<br/>
Znak do wstawienia do określonego bufora lub `EOF`.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie powiedzie się, zwraca `EOF`. W przeciwnym razie, jeśli  *\_Meta* == `EOF`, zwraca niektóre wartości innych niż `EOF`. W przeciwnym razie zwraca  *\_Meta*.

### <a name="remarks"></a>Uwagi

Jeśli  *\_Meta* ! = `EOF`, chronionych wirtualna funkcja składowa próbuje Wstaw element `(char)_Meta` do buforu danych wyjściowych. Jego można to zrobić na różne sposoby:

- W przypadku pozycji zapisu jest dostępny, można przechowywać element w określonej pozycji zapisu i zwiększyć wskaźnik następnej dla buforu danych wyjściowych.

- Jeśli tryb przechowywanych strstreambuf — mówi, że kontrolowanej sekwencji jest modyfikowalny, rozszerzalnej i nie zamrożone, funkcja udostępnić pozycji zapisu, przydzielając nowe dla buforu danych wyjściowych. Rozszerzanie bufora wyjściowego w ten sposób rozszerzają wszelkie skojarzone buforu wejściowego.

## <a name="pbackfail"></a>  strstreambuf::pbackfail

Funkcja chronionych wirtualna elementu członkowskiego, która próbuje odłożyć element do strumienia wejściowego, a następnie sprawia, że bieżący element (wskazywany przez wskaźnik następnej).

```cpp
virtual int pbackfail(int _Meta = EOF);
```

### <a name="parameters"></a>Parametry

*_Meta*<br/>
Znak do wstawienia do określonego bufora lub `EOF`.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie powiedzie się, zwraca `EOF`. W przeciwnym razie, jeśli  *\_Meta* == `EOF`, zwraca niektóre wartości innych niż `EOF`. W przeciwnym razie zwraca  *\_Meta*.

### <a name="remarks"></a>Uwagi

Funkcja chroniony element członkowski wirtualnego próbuje odłożyć element do buforu wejściowego, a następnie bieżącego elementu (wskazywany przez wskaźnik następnej).

Jeśli  *\_Meta* == `EOF`, element do usunięcia jest skutecznie już w strumieniu przed bieżącego elementu. W przeciwnym razie ten element został zastąpiony `ch = (char)_Meta`. Funkcję można odłożyć element na różne sposoby:

- Jeśli pozycja putback — i element tam przechowywane w porównaniu równa `ch`, jego dekrementacja wskaźnik następnej dla buforu danych wejściowych.

- Jeśli pozycja putback — jest dostępna, a jeśli tryb strstreambuf — jest w kontrolowanej sekwencji jest modyfikowalny, funkcja może `ch` putback — pozycja i dekrementacji wskaźnik następnej dla buforu danych wejściowych.

## <a name="pcount"></a>  strstreambuf::pcount

Zwraca liczbę elementów zapisywane w kontrolowanej sekwencji.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Wartość zwracana

Licznik liczby elementów zapisywane w kontrolowanej sekwencji.

### <a name="remarks"></a>Uwagi

W szczególności jeśli [pptr —](../standard-library/basic-streambuf-class.md#pptr) jest pustym wskaźnikiem, funkcja zwraca wartość zero. W przeciwnym razie zwraca `pptr`  -  [pbase —](../standard-library/basic-streambuf-class.md#pbase).

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

## <a name="seekoff"></a>  strstreambuf::seekoff

Funkcja chronionych wirtualna elementu członkowskiego, która próbuje zmienić dla strumieni kontrolowanego bieżącej pozycji.

```cpp
virtual streampos seekoff(streamoff _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Off*<br/>
Położenie do wyszukania dla względem *_Way*.

*_Way*<br/>
Punkt początkowy dla operacji przesunięcia. Zobacz [seekdir](../standard-library/ios-base-class.md#seekdir) uzyskać odpowiednie wartości.

*_Which*<br/>
Określa tryb pozycję wskaźnika. Wartość domyślna to umożliwia modyfikowanie, Odczyt i zapis pozycji.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, w jednej zmiany lub strumienia obie pozycje, zwraca położenie wynikowy strumień. W przeciwnym razie nie powiedzie się i zwraca pozycję nieprawidłowy strumień.

### <a name="remarks"></a>Uwagi

Funkcja chroniony element członkowski wirtualnego usiłują alter dla strumieni kontrolowanego bieżącej pozycji. W przypadku obiektu strstreambuf — klasa pozycji strumienia składa się wyłącznie z przesunięciu strumienia. Przesunięcia zero wskazuje pierwszego elementu w kontrolowanej sekwencji.

Nowa pozycja jest określany w następujący sposób:

- Jeśli `_Way == ios_base::beg`, nowe położenie jest na początku strumienia plus *_Off*.

- Jeśli `_Way == ios_base::cur`, nowe położenie jest bieżącą pozycję w strumieniu oraz *_Off*.

- Jeśli `_Way == ios_base::end`, nowe położenie jest koniec strumienia plus *_Off*.

Jeśli `_Which & ios_base::in` jest różna od zera i istnieje buforu wejściowego, funkcja zmienia pozycję dalej do odczytu w buforze wejściowym. Jeśli `_Which & ios_base::out` również jest różna od zera, `_Way != ios_base::cur`i istnieje bufor wyjściowy, funkcja ustawia również następnej pozycji, aby zapisać dopasowania następnej pozycji, aby odczytać.

W przeciwnym razie, jeśli `_Which & ios_base::out` jest różna od zera i bufor wyjściowy istnieje, funkcja zmienia następnej pozycji, aby zapisać w buforze danych wyjściowych. W przeciwnym razie pozycjonowania kończy się niepowodzeniem. Pozycjonowania operacja została wykonana pomyślnie wynikowy pozycji strumienia musi znajdować się w kontrolowanej sekwencji.

## <a name="seekpos"></a>  strstreambuf::seekpos

Funkcja chronionych wirtualna elementu członkowskiego, która próbuje zmienić dla strumieni kontrolowanego bieżącej pozycji.

```cpp
virtual streampos seekpos(streampos _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*<br/>
Położenie do wyszukania dla.

*_Which*<br/>
Określa tryb pozycję wskaźnika. Wartość domyślna to umożliwia modyfikowanie, Odczyt i zapis pozycji.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, w jednej zmiany lub strumienia obie pozycje, zwraca położenie wynikowy strumień. W przeciwnym razie nie powiedzie się i zwraca pozycję nieprawidłowy strumień. Aby określić, jeśli pozycja strumienia jest nieprawidłowa, porównaj wartość zwracaną z `pos_type(off_type(-1))`.

### <a name="remarks"></a>Uwagi

Funkcja chroniony element członkowski wirtualnego usiłują alter dla strumieni kontrolowanego bieżącej pozycji. W przypadku obiektu strstreambuf — klasa pozycji strumienia składa się wyłącznie z przesunięciu strumienia. Przesunięcia zero wskazuje pierwszego elementu w kontrolowanej sekwencji. Nowa pozycja jest określana przez *_Sp*.

Jeśli `_Which`  &  **ios_base::in** jest różna od zera i istnieje buforu wejściowego, funkcja zmienia pozycję dalej do odczytu w buforze wejściowym. Jeśli `_Which`  &  `ios_base::out` jest różna od zera i bufor wyjściowy istnieje, funkcja ustawia również następnej pozycji, aby zapisać dopasowania następnej pozycji, aby odczytać. W przeciwnym razie, jeśli `_Which`  &  `ios_base::out` jest różna od zera i bufor wyjściowy istnieje, funkcja zmienia następnej pozycji, aby zapisać w buforze danych wyjściowych. W przeciwnym razie pozycjonowania kończy się niepowodzeniem. Pozycjonowania operacja została wykonana pomyślnie wynikowy pozycji strumienia musi znajdować się w kontrolowanej sekwencji.

## <a name="str"></a>  strstreambuf::str

Wywołania [freeze](#freeze), a następnie zwraca wskaźnik do początku kontrolowanej sekwencji.

```cpp
char *str();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik na początek kontrolowanej sekwencji.

### <a name="remarks"></a>Uwagi

Element o wartości null nie kończący istnieje, chyba że jawnie wstawieniu.

### <a name="example"></a>Przykład

Zobacz [strstreambuf::freeze](#freeze) dla przykładu, który używa **str**.

## <a name="strstreambuf"></a>  strstreambuf::strstreambuf

Tworzy obiekt typu `strstreambuf`.

```cpp
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

*_Allocfunc*<br/>
Funkcja używana można przydzielić bufora pamięci.

*Liczba*<br/>
Określa długość bufor wskazywany przez *_Getptr*. Jeśli *_Getptr* nie jest argument (pierwszy Konstruktor formularz) sugerowane alokacji rozmiar buforów.

*_Freefunc*<br/>
Funkcja używana, aby zwolnić pamięć buforu.

*_Getptr*<br/>
Bufor używany do wprowadzania danych.

*_Putptr*<br/>
Bufor używany dla danych wyjściowych.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor przechowuje wskaźnik zerowy w wszystkie wskaźniki kontrolowanie buforu wejściowego, buforu wyjściowego i strstreambuf — alokacji. Ustawia tryb przechowywanych strstreambuf — aby argumentami modyfikowalnymi i rozszerzalnej kontrolowanej sekwencji. Również akceptuje *liczba* jako sugerowane początkowy rozmiar alokacji.

Drugi Konstruktor zachowuje się jak pierwsza strona, z tą różnicą, że przechowuje  *\_Allocfunc* jako wskaźnik do funkcji do wywołania do przydzielania pamięci i  *\_Freefunc* jak wskaźnik Aby funkcja do wywołania, aby zwolnić tego magazynu.

Trzy konstruktory:

```cpp
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

zawsze zachowują się jak pierwsza strona, z tą różnicą, że `_Getptr` wyznacza obiektu array, używane do przechowywania kontrolowanej sekwencji. (Dlatego nie należy wskaźnikiem typu null.) Liczba elementów, które *N* w tablicy jest określany w następujący sposób:

- Jeśli (`count` > 0), następnie *N* jest `count`.

- Jeśli (`count` == 0), następnie *N* jest `strlen`(( **const** `char` *) `_Getptr` ).

- Jeśli (`count` < 0), następnie *N* jest **INT_MAX**.

Jeśli `_Putptr` jest pustym wskaźnikiem, funkcja ustanawia po prostu buforu wejściowego, wykonując:

```cpp
setg(_Getptr,
    _Getptr,
    _Getptr + N);
```

W przeciwnym razie ustanawia bufory wejściowe i wyjściowe, wykonując:

```cpp
setg(_Getptr,
    _Getptr,
    _Putptr);

setp(_Putptr,
    _Getptr + N);
```

W tym przypadku `_Putptr` musi być w interwale [ `_Getptr`, `_Getptr`  +  *N*].

Na koniec trzy konstruktory:

```cpp
strstreambuf(const char *_Getptr,
    streamsize count);

strstreambuf(const signed char *_Getptr,
    streamsize count);

strstreambuf(const unsigned char *_Getptr,
    streamsize count);
```

wszystko działa tak samo, jak:

```cpp
streambuf((char *)_Getptr, count);
```

poza tym, że tryb przechowywanych sprawia, że kontrolowanej sekwencji można modyfikować ani rozszerzalne.

## <a name="underflow"></a>  strstreambuf::underflow

Chroniony funkcją wirtualną można wyodrębnić bieżącego elementu ze strumienia wejściowego.

```cpp
virtual int underflow();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie powiedzie się, zwraca `EOF`. W przeciwnym razie zwraca bieżącego elementu w strumieniu wejściowym przekonwertować zgodnie z powyższym opisem.

### <a name="remarks"></a>Uwagi

Chronione wirtualna funkcja składowa usiłują wyodrębnić bieżącego elementu `ch` z buforu wejściowego, następnie przejdź bieżącej pozycji strumienia i zwracać element jako (`int`) (`unsigned char`) **ch**. Jego można to zrobić w tylko jednym ze sposobów: pozycję odczytu jest dostępny, dopiero po `ch` elementu przechowywanego w pozycji odczytu i przesuwa wskaźnik następnej dla buforu danych wejściowych.

## <a name="see-also"></a>Zobacz także

[streambuf](../standard-library/streambuf-typedefs.md#streambuf)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
