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
ms.openlocfilehash: 28399a1cd55407aadbc5d59e1e835892218ad0c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376607"
---
# <a name="strstreambuf-class"></a>strstreambuf — Klasa

W tym artykule opisano bufor strumienia, który kontroluje transmisję elementów do i z sekwencji elementów przechowywanych w obiekcie tablicy **char.**

## <a name="syntax"></a>Składnia

```cpp
class strstreambuf : public streambuf
```

## <a name="remarks"></a>Uwagi

W zależności od sposobu konstruowania obiektu, może być przydzielany, rozszerzany i zwalniany w razie potrzeby, aby uwzględnić zmiany w sekwencji.

Obiekt klasy `strstreambuf` przechowuje kilka bitów informacji `strstreambuf` o trybie jako jego tryb. Te bity wskazują, czy kontrolowana sekwencja:

- Został przydzielony i musi zostać ostatecznie uwolniony.

- Można go modyfikować.

- Można go rozszerzyć, przenosząc magazyn.

- Został zamrożony i dlatego musi zostać odblokowany, zanim obiekt zostanie zniszczony lub uwolniony (jeśli został przydzielony) przez agencję inną niż obiekt.

Kontrolowana sekwencja, która jest zablokowana, nie może być modyfikowana ani rozszerzana, niezależnie od stanu tych oddzielnych bitów trybu.

Obiekt przechowuje również wskaźniki do `strstreambuf` dwóch funkcji, które kontrolują alokacji. Jeśli są to wskaźniki null, obiekt opracowuje własną metodę przydzielania i zwalniania magazynu dla kontrolowanej sekwencji.

> [!NOTE]
> Ta klasa jest przestarzała. Rozważ użycie [stringbuf](../standard-library/sstream-typedefs.md#stringbuf) lub [wstringbuf](../standard-library/sstream-typedefs.md#wstringbuf) zamiast.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Strstreambuf](#strstreambuf)|Konstruuje obiekt `strstreambuf`typu .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Zamrozić](#freeze)|Powoduje, że bufor strumienia jest niedostępny za pośrednictwem operacji buforu strumienia.|
|[Przepełnienie](#overflow)|Chroniona funkcja wirtualna, która może być wywoływana po wstawieniu nowego znaku do pełnego buforu.|
|[pbackfail](#pbackfail)|Funkcja chronionego elementu członkowskiego wirtualnego, która próbuje umieścić z powrotem element do strumienia wejściowego, a następnie uczynić go bieżącym elementem (wskazywała na następny wskaźnik).|
|[pcount (liczba pcount)](#pcount)|Zwraca liczbę elementów zapisanych w kontrolowanej sekwencji.|
|[poszukiwanie](#seekoff)|Funkcja chronionego elementu członkowskiego wirtualnego, która próbuje zmienić bieżące pozycje dla kontrolowanych strumieni.|
|[seekpos](#seekpos)|Funkcja chronionego elementu członkowskiego wirtualnego, która próbuje zmienić bieżące pozycje dla kontrolowanych strumieni.|
|[Str](#str)|Wywołania [freeze](#freeze), a następnie zwraca wskaźnik na początku kontrolowanej sekwencji.|
|[Niedomiar](#underflow)|Chroniona funkcja wirtualna, aby wyodrębnić bieżący element ze strumienia wejściowego.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<strstream>

**Przestrzeń nazw:** std

## <a name="strstreambuffreeze"></a><a name="freeze"></a>strstreambuf::zamrożenie

Powoduje, że bufor strumienia jest niedostępny za pośrednictwem operacji buforu strumienia.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Parametry

*_Freezeit*\
**Bool** wskazujący, czy strumień ma zostać zamrożony.

### <a name="remarks"></a>Uwagi

Jeśli *_Freezeit* jest true, funkcja zmienia `strstreambuf` tryb przechowywany, aby kontrolowana sekwencja zamrożone. W przeciwnym razie sprawia, że kontrolowana sekwencja nie jest zamrożona.

[str](#str) implikuje `freeze`.

> [!NOTE]
> Zamrożony bufor nie zostanie `strstreambuf` uwolniony podczas niszczenia. Należy odblokować bufor, zanim zostanie on zwolniony, aby uniknąć przecieku pamięci.

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

## <a name="strstreambufoverflow"></a><a name="overflow"></a>strstreambuf::przepełnienie

Chroniona funkcja wirtualna, która może być wywoływana po wstawieniu nowego znaku do pełnego buforu.

```cpp
virtual int overflow(int _Meta = EOF);
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak, który ma być `EOF`wstawiany do buforu lub .

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może `EOF`zakończyć się pomyślnie, zwraca . W przeciwnym * \_* razie, jeśli Meta == `EOF` `EOF`, zwraca pewną wartość inną niż . W przeciwnym * \_* razie zwraca Meta .

### <a name="remarks"></a>Uwagi

Jeśli * \_Meta* `EOF`!= , funkcja chronionego elementu `(char)_Meta` członkowskiego wirtualnego próbuje wstawić element do buforu wyjściowego. Może to zrobić na różne sposoby:

- Jeśli pozycja zapisu jest dostępna, może przechowywać element w pozycji zapisu i zwiększać następny wskaźnik dla buforu wyjściowego.

- Jeśli w trybie strstreambuf przechowywane mówi, że kontrolowana sekwencja jest modyfikowalna, rozszerzalna i nie jest zablokowana, funkcja może udostępnić pozycję zapisu, przydzielając nowe dla buforu wyjściowego. Rozszerzenie buforu wyjściowego w ten sposób rozszerza również wszelkie skojarzone buforu wejściowego.

## <a name="strstreambufpbackfail"></a><a name="pbackfail"></a>strstreambuf::pbackfail

Funkcja chronionego elementu członkowskiego wirtualnego, która próbuje umieścić z powrotem element do strumienia wejściowego, a następnie sprawia, że bieżący element (wskazywał na następny wskaźnik).

```cpp
virtual int pbackfail(int _Meta = EOF);
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak, który ma być `EOF`wstawiany do buforu lub .

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może `EOF`zakończyć się pomyślnie, zwraca . W przeciwnym * \_* razie, jeśli Meta == `EOF` `EOF`, zwraca pewną wartość inną niż . W przeciwnym * \_* razie zwraca Meta .

### <a name="remarks"></a>Uwagi

Funkcja chronionego elementu członkowskiego wirtualnego próbuje umieścić z powrotem element do buforu wejściowego, a następnie uczynić go bieżącym elementem (wskazywał na następny wskaźnik).

Jeśli * \_Meta* == `EOF`, element do odepchnięcia jest skutecznie ten już w strumieniu przed bieżącym elementem. W przeciwnym razie ten `ch = (char)_Meta`element zostanie zastąpiony przez . Funkcja może umieścić z powrotem element na różne sposoby:

- Jeśli pozycja odłożenia jest dostępna, a przechowywany `ch`tam element porównuje się równy , może zniegować następny wskaźnik dla buforu wejściowego.

- Jeśli pozycja putback jest dostępna, a tryb strstreambuf mówi, że kontrolowana `ch` sekwencja jest modyfikowalna, funkcja może przechowywać w pozycji putback i zmniejszać następny wskaźnik dla buforu wejściowego.

## <a name="strstreambufpcount"></a><a name="pcount"></a>strstreambuf::pcount

Zwraca liczbę elementów zapisanych w kontrolowanej sekwencji.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów zapisanych w kontrolowanej sekwencji.

### <a name="remarks"></a>Uwagi

W szczególności jeśli [pptr](../standard-library/basic-streambuf-class.md#pptr) jest wskaźnikiem null, funkcja zwraca zero. W przeciwnym `pptr`  - razie zwraca [pbase](../standard-library/basic-streambuf-class.md#pbase).

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

## <a name="strstreambufseekoff"></a><a name="seekoff"></a>strstreambuf::seekoff

Funkcja chronionego elementu członkowskiego wirtualnego, która próbuje zmienić bieżące pozycje dla kontrolowanych strumieni.

```cpp
virtual streampos seekoff(streamoff _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_off*\
Stanowisko do poszukiwania w stosunku do *_Way*.

*_way*\
Punktem wyjścia dla operacji odsunięcia. Zobacz [seekdir](../standard-library/ios-base-class.md#seekdir) dla możliwych wartości.

*_Which*\
Określa tryb położenia wskaźnika. Domyślnie można zmodyfikować pozycje odczytu i zapisu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja powiedzie się w zmianie jednej lub obu pozycji strumienia, zwraca wynikową pozycję strumienia. W przeciwnym razie kończy się niepowodzeniem i zwraca nieprawidłową pozycję strumienia.

### <a name="remarks"></a>Uwagi

Funkcja chronionego elementu członkowskiego wirtualnego stara się zmieniać bieżące pozycje dla kontrolowanych strumieni. Dla obiektu klasy strstreambuf, położenie strumienia składa się wyłącznie z przesunięcia strumienia. Offset zero wyznacza pierwszy element kontrolowanej sekwencji.

Nowe stanowisko określa się w następujący sposób:

- Jeśli `_Way == ios_base::beg`nowa pozycja jest początkiem strumienia plus *_Off*.

- Jeśli `_Way == ios_base::cur`nowa pozycja to bieżąca pozycja strumienia plus *_Off*.

- Jeśli `_Way == ios_base::end`nowa pozycja to koniec strumienia plus *_Off*.

Jeśli `_Which & ios_base::in` jest niezerowy i istnieje bufor wejściowy, funkcja zmienia następną pozycję do odczytu w buforze wejściowym. Jeśli `_Which & ios_base::out` jest również niezerowy, `_Way != ios_base::cur`a bufor wyjściowy istnieje, funkcja ustawia również następną pozycję do zapisu, aby dopasować następną pozycję do odczytu.

W przeciwnym `_Which & ios_base::out` razie, jeśli jest niezerowy i istnieje bufor wyjściowy, funkcja zmienia następną pozycję do zapisu w buforze wyjściowym. W przeciwnym razie operacja pozycjonowania kończy się niepowodzeniem. Aby operacja pozycjonowania powiodła się, wynikowa pozycja strumienia musi znajdować się w kontrolowanej sekwencji.

## <a name="strstreambufseekpos"></a><a name="seekpos"></a>strstreambuf::seekpos

Funkcja chronionego elementu członkowskiego wirtualnego, która próbuje zmienić bieżące pozycje dla kontrolowanych strumieni.

```cpp
virtual streampos seekpos(streampos _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*\
Stanowisko do poszukiwania.

*_Which*\
Określa tryb położenia wskaźnika. Domyślnie można zmodyfikować pozycje odczytu i zapisu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja powiedzie się w zmianie jednej lub obu pozycji strumienia, zwraca wynikową pozycję strumienia. W przeciwnym razie kończy się niepowodzeniem i zwraca nieprawidłową pozycję strumienia. Aby ustalić, czy pozycja strumienia jest `pos_type(off_type(-1))`nieprawidłowa, porównaj wartość zwracaną z programem .

### <a name="remarks"></a>Uwagi

Funkcja chronionego elementu członkowskiego wirtualnego stara się zmieniać bieżące pozycje dla kontrolowanych strumieni. Dla obiektu klasy strstreambuf, położenie strumienia składa się wyłącznie z przesunięcia strumienia. Offset zero wyznacza pierwszy element kontrolowanej sekwencji. Nowa pozycja jest określana przez *_Sp*.

Jeśli `_Which`  &  **ios_base::in** jest niezerowy i istnieje bufor wejściowy, funkcja zmienia następną pozycję do odczytu w buforze wejściowym. `_Which`  &  Jeśli `ios_base::out` jest niezerowy i istnieje bufor wyjściowy, funkcja ustawia również następną pozycję do zapisu, aby dopasować następną pozycję do odczytu. W przeciwnym `_Which`  &  `ios_base::out` razie, jeśli jest niezerowy i istnieje bufor wyjściowy, funkcja zmienia następną pozycję do zapisu w buforze wyjściowym. W przeciwnym razie operacja pozycjonowania kończy się niepowodzeniem. Aby operacja pozycjonowania powiodła się, wynikowa pozycja strumienia musi znajdować się w kontrolowanej sekwencji.

## <a name="strstreambufstr"></a><a name="str"></a>strstreambuf::str

Wywołania [freeze](#freeze), a następnie zwraca wskaźnik na początku kontrolowanej sekwencji.

```cpp
char *str();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do początku kontrolowanej sekwencji.

### <a name="remarks"></a>Uwagi

Nie istnieje element kończący null, chyba że jawnie wstawić jeden.

### <a name="example"></a>Przykład

Zobacz [strstreambuf::freeze](#freeze) dla próbki, która używa **str**.

## <a name="strstreambufstrstreambuf"></a><a name="strstreambuf"></a>strstreambuf::strstreambuf

Konstruuje obiekt `strstreambuf`typu .

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

*_Allocfunc*\
Funkcja używana do przydzielania pamięci buforowej.

*Liczba*\
Określa długość buforu wskazywionego przez *_Getptr*. Jeśli *_Getptr* nie jest argumentem (formularz pierwszego konstruktora), sugerowany rozmiar alokacji dla buforów.

*_Freefunc*\
Funkcja używana do zwalniania pamięci buforowej.

*_Getptr*\
Bufor używany do wprowadzania danych.

*_Putptr*\
Bufor używany do produkcji wyjściowej.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor przechowuje wskaźnik null we wszystkich wskaźników sterujących buforu wejściowego, buforu wyjściowego i alokacji strstreambuf. Ustawia przechowywany tryb strstreambuf, aby kontrolowana sekwencja była konfigurowalna i rozszerzalna. Akceptuje również *liczbę* jako sugerowany rozmiar alokacji początkowej.

Drugi konstruktor zachowuje się jak pierwszy, z tą różnicą, że przechowuje * \_Allocfunc* jako wskaźnik do funkcji do wywołania przydzielić magazynu i * \_Freefunc* jako wskaźnik do funkcji, aby wywołać, aby zwolnić tego magazynu.

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

również zachowywać się jak `_Getptr` pierwszy, z tą różnicą, że wyznacza obiekt tablicy używane do przechowywania kontrolowanej sekwencji. (W związku z tym nie może być wskaźnik null.) Liczba elementów *N* w tablicy jest określana w następujący sposób:

- Jeśli`count` (> 0), to *N* N `count`jest .

- Jeśli`count` ( == 0), `strlen`to *N* jest `_Getptr` ( **( const** `char` *) ).

- Jeśli`count` ( < 0), to *N* jest **INT_MAX**.

Jeśli `_Putptr` jest wskaźnikiem zerowym, funkcja ustanawia tylko bufor wejściowy, wykonując:

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

W takim `_Putptr` przypadku musi znajdować `_Getptr`się `_Getptr`  + w przedziale [ , *N*].

Na koniec trzech konstruktorów:

```cpp
strstreambuf(const char *_Getptr,
    streamsize count);

strstreambuf(const signed char *_Getptr,
    streamsize count);

strstreambuf(const unsigned char *_Getptr,
    streamsize count);
```

wszystkie zachowują się tak samo jak:

```cpp
streambuf((char *)_Getptr, count);
```

z tą różnicą, że tryb przechowywany sprawia, że kontrolowana sekwencja nie jest modyfikowalna ani rozszerzalna.

## <a name="strstreambufunderflow"></a><a name="underflow"></a>strstreambuf::niedopełnienie

Chroniona funkcja wirtualna, aby wyodrębnić bieżący element ze strumienia wejściowego.

```cpp
virtual int underflow();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może `EOF`zakończyć się pomyślnie, zwraca . W przeciwnym razie zwraca bieżący element w strumieniu wejściowym, przekonwertowany w sposób opisany powyżej.

### <a name="remarks"></a>Uwagi

Chroniona funkcja wirtualnego elementu członkowskiego stara się `ch` wyodrębnić bieżący element z buforu wejściowego, a`int`następnie`unsigned char`przejść bieżącą pozycję strumienia i zwrócić element jako ( )( ) **ch**. Może to zrobić tylko w jeden sposób: jeśli pozycja `ch` odczytu jest dostępna, przyjmuje jako element przechowywany w pozycji odczytu i przesuwa następny wskaźnik dla buforu wejściowego.

## <a name="see-also"></a>Zobacz też

[streambuf](../standard-library/streambuf-typedefs.md#streambuf)\
[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
