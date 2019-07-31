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
ms.openlocfilehash: f24d8fe99bc211e026172e42669cf5e430ad31e8
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459075"
---
# <a name="strstreambuf-class"></a>strstreambuf — Klasa

Opisuje bufor strumienia, który kontroluje przekazywanie elementów do i z sekwencji elementów przechowywanych w obiekcie tablicy **char** .

## <a name="syntax"></a>Składnia

```cpp
class strstreambuf : public streambuf
```

## <a name="remarks"></a>Uwagi

W zależności od sposobu konstruowania obiektu można mu przydzielać, rozszerzać i zwalniać w razie potrzeby w celu uwzględnienia zmian w sekwencji.

Obiekt klasy `strstreambuf` przechowuje kilka bitów informacji o trybie jako ich `strstreambuf` tryb. Te bity wskazują, czy kontrolowana sekwencja:

- Został przydzielony i musi być ostatecznie zwolniony.

- Jest modyfikowalny.

- Program jest rozszerzalny przez ponowną alokację magazynu.

- Zostało zamrożone i dlatego musi zostać odblokowane przed zniszczeniem lub zwolnieniem obiektu (jeśli jest przydzielone) przez Agencję inną niż obiekt.

Nie można zmodyfikować ani rozszerzyć kontrolowanej sekwencji, bez względu na stan poszczególnych bitów trybu.

Obiekt przechowuje również wskaźniki do dwóch funkcji kontrolujących `strstreambuf` alokację. Jeśli są to wskaźniki o wartości null, obiekt opracowuje własną metodę alokowania i zwalniania magazynu dla kontrolowanej sekwencji.

> [!NOTE]
> Ta klasa jest przestarzała. Zamiast tego Rozważ użycie [stringbuf —](../standard-library/sstream-typedefs.md#stringbuf) lub [wstringbuf —](../standard-library/sstream-typedefs.md#wstringbuf) .

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[strstreambuf](#strstreambuf)|Konstruuje obiekt typu `strstreambuf`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[Funkcja](#freeze)|Powoduje, że bufor strumienia nie jest dostępny za pomocą operacji buforu strumienia.|
|[overflow](#overflow)|Chroniona funkcja wirtualna, która może być wywoływana, gdy nowy znak zostanie wstawiony do pełnego buforu.|
|[pbackfail](#pbackfail)|Chroniona funkcja wirtualna elementu członkowskiego, która próbuje umieścić element w strumieniu wejściowym, a następnie uczynić go bieżącym elementem (wskazywanym przez następny wskaźnik).|
|[pcount](#pcount)|Zwraca liczbę elementów, które są zapisywane w kontrolowanej sekwencji.|
|[seekoff](#seekoff)|Chroniona funkcja wirtualna elementu członkowskiego, która próbuje zmienić bieżące położenie dla kontrolowanych strumieni.|
|[seekpos](#seekpos)|Chroniona funkcja wirtualna elementu członkowskiego, która próbuje zmienić bieżące położenie dla kontrolowanych strumieni.|
|[str](#str)|Wywołania [zawieszają](#freeze)się, a następnie zwracają wskaźnik do początku kontrolowanej sekwencji.|
|[underflow](#underflow)|Chroniona funkcja wirtualna do wyodrębnienia bieżącego elementu ze strumienia wejściowego.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<strstream >

**Przestrzeń nazw:** std

## <a name="freeze"></a>strstreambuf:: Zablokuj

Powoduje, że bufor strumienia nie jest dostępny za pomocą operacji buforu strumienia.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Parametry

*_Freezeit*\
Wartość **logiczna** wskazująca, czy strumień ma być zablokowany.

### <a name="remarks"></a>Uwagi

Jeśli *_Freezeit* ma wartość true, funkcja zmienia tryb przechowywany `strstreambuf` , aby umożliwić zamrożoną sekwencję. W przeciwnym razie ta kolejność nie jest zamrożona.

[str](#str) oznacza `freeze`.

> [!NOTE]
> Zamrożony bufor nie zostanie zwolniony podczas `strstreambuf` niszczenia. Przed zwolnieniem buforu należy odblokować go, aby uniknąć przecieku pamięci.

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

## <a name="overflow"></a>strstreambuf:: overflow

Chroniona funkcja wirtualna, która może być wywoływana, gdy nowy znak zostanie wstawiony do pełnego buforu.

```cpp
virtual int overflow(int _Meta = EOF);
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak, który ma zostać wstawiony do buforu lub `EOF`.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może się powieść `EOF`, zwraca wartość. W przeciwnym razie zwraca wartość inną niż .`EOF`  *\_*  == `EOF` W przeciwnym razie zwraca  *\_meta*.

### <a name="remarks"></a>Uwagi

`EOF`Jeśli  *\_meta* ! =, chroniona funkcja wirtualna elementu członkowskiego próbuje wstawić `(char)_Meta` element do buforu wyjściowego. Można to zrobić na różne sposoby:

- Jeśli dostępna jest pozycja zapisu, może ona przechowywać element w pozycji zapisu i zwiększać następny wskaźnik dla buforu wyjściowego.

- Jeśli w trybie zapisanego strstreambuf jest wyświetlana kontrolowana sekwencja jest modyfikowalna, rozszerzalna i niezamrożona, funkcja może ustawić pozycję zapisu, przydzielając nowe dla buforu wyjściowego. Rozszerzanie buforu wyjściowego w ten sposób rozszerza również każdy skojarzony bufor wejściowy.

## <a name="pbackfail"></a>strstreambuf: niepowodzenie:p

Chroniona funkcja wirtualna elementu członkowskiego próbująca umieścić element w strumieniu wejściowym, a następnie sprawia, że staje się on bieżącym elementem (wskazywanym przez następny wskaźnik).

```cpp
virtual int pbackfail(int _Meta = EOF);
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak, który ma zostać wstawiony do buforu lub `EOF`.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może się powieść `EOF`, zwraca wartość. W przeciwnym razie zwraca wartość inną niż .`EOF`  *\_*  == `EOF` W przeciwnym razie zwraca  *\_meta*.

### <a name="remarks"></a>Uwagi

Chroniona funkcja wirtualna elementu członkowskiego próbuje umieścić element w buforze wejściowym, a następnie uczynić go bieżącym elementem (wskazywanym przez następny wskaźnik).

*Jeśli\_meta*,elementdo`EOF`wypchnięcia jest efektywnie tym, że jest już w strumieniu przed bieżącym elementem. ==  W przeciwnym razie ten element zostanie zastąpiony przez `ch = (char)_Meta`. Funkcja może umieścić element na różne sposoby:

- Jeśli pozycja putback jest dostępna, a element przechowywany jest porównuje równy `ch`, może zmniejszyć następny wskaźnik dla buforu wejściowego.

- Jeśli pozycja putback jest dostępna i jeśli tryb strstreambuf wskazuje, że kontrolowana sekwencja jest modyfikowalna, funkcja może być przechowywana `ch` w pozycji putback i zmniejszać następny wskaźnik dla buforu wejściowego.

## <a name="pcount"></a>strstreambuf: liczba:p

Zwraca liczbę elementów, które są zapisywane w kontrolowanej sekwencji.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów zapisywana w kontrolowanej sekwencji.

### <a name="remarks"></a>Uwagi

W przypadku, gdy [pptr](../standard-library/basic-streambuf-class.md#pptr) jest wskaźnikiem typu null, funkcja zwraca wartość zero. W przeciwnym razie zwraca `pptr`  -  [pbase](../standard-library/basic-streambuf-class.md#pbase).

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

Chroniona funkcja wirtualna elementu członkowskiego, która próbuje zmienić bieżące położenie dla kontrolowanych strumieni.

```cpp
virtual streampos seekoff(streamoff _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Off*\
Pozycja do wyszukiwania względem *_Way*.

*_Way*\
Punkt początkowy dla operacji przesunięcia. Zobacz [seekdir](../standard-library/ios-base-class.md#seekdir) , aby uzyskać możliwe wartości.

*_Which*\
Określa tryb dla pozycji wskaźnika. Wartość domyślna to umożliwienie modyfikacji pozycji odczytu i zapisu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie w przypadku zmiany obu lub obu pozycji strumienia, zwraca wynikową pozycję strumienia. W przeciwnym razie kończy się niepowodzeniem i zwraca nieprawidłową pozycję strumienia.

### <a name="remarks"></a>Uwagi

Chroniona wirtualna funkcja członkowska przedsięwzięciach, aby zmienić bieżące położenia dla kontrolowanych strumieni. Dla obiektu klasy strstreambuf pozycja strumienia składa się wyłącznie z przesunięcia strumienia. Przesunięcie zero oznacza pierwszy element kontrolowanej sekwencji.

Nowa pozycja jest określana w następujący sposób:

- Jeśli `_Way == ios_base::beg`Nowa pozycja jest początkiem strumienia i *_Off*.

- Jeśli `_Way == ios_base::cur`Nowa pozycja jest bieżącym położeniem strumienia i *_Off*.

- Jeśli `_Way == ios_base::end`Nowa pozycja jest końcem strumienia i *_Off*.

Jeśli `_Which & ios_base::in` jest różna od zera, a bufor wejściowy istnieje, funkcja zmienia następną pozycję do odczytu w buforze wejściowym. Jeśli `_Which & ios_base::out` jest również `_Way != ios_base::cur`różna od zera, a bufor wyjściowy istnieje, funkcja ustawia również następną pozycję do zapisu w celu dopasowania do kolejnej pozycji do odczytu.

W przeciwnym razie `_Which & ios_base::out` , jeśli jest różna od zera i istnieje bufor wyjściowy, funkcja zmienia następną pozycję do zapisu w buforze wyjściowym. W przeciwnym razie operacja pozycjonowania zakończy się niepowodzeniem. Aby operacja pozycjonowania zakończyła się pomyślnie, pochodząca pozycja w strumieniu musi znajdować się w kontrolowanej sekwencji.

## <a name="seekpos"></a>strstreambuf:: seekpos

Chroniona funkcja wirtualna elementu członkowskiego, która próbuje zmienić bieżące położenie dla kontrolowanych strumieni.

```cpp
virtual streampos seekpos(streampos _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*\
Pozycja do wyszukania.

*_Which*\
Określa tryb dla pozycji wskaźnika. Wartość domyślna to umożliwienie modyfikacji pozycji odczytu i zapisu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie w przypadku zmiany obu lub obu pozycji strumienia, zwraca wynikową pozycję strumienia. W przeciwnym razie kończy się niepowodzeniem i zwraca nieprawidłową pozycję strumienia. Aby określić, czy pozycja strumienia jest nieprawidłowa, porównaj wartość zwracaną z `pos_type(off_type(-1))`.

### <a name="remarks"></a>Uwagi

Chroniona wirtualna funkcja członkowska przedsięwzięciach, aby zmienić bieżące położenia dla kontrolowanych strumieni. Dla obiektu klasy strstreambuf pozycja strumienia składa się wyłącznie z przesunięcia strumienia. Przesunięcie zero oznacza pierwszy element kontrolowanej sekwencji. Nowa pozycja jest określana przez *_Sp*.

Jeśli `_Which` ios_base &  **:: in** ma wartość różną od zera, a bufor wejściowy istnieje, funkcja zmienia następną pozycję do odczytu w buforze wejściowym. Jeśli `_Which` wartośćjestróżna`ios_base::out` od zera i istnieje bufor wyjściowy, funkcja ustawia również następną pozycję do zapisu w celu dopasowania do kolejnej pozycji do odczytu.  &  W przeciwnym razie `_Which` , jeśli  &  `ios_base::out` jest różna od zera i istnieje bufor wyjściowy, funkcja zmienia następną pozycję do zapisu w buforze wyjściowym. W przeciwnym razie operacja pozycjonowania zakończy się niepowodzeniem. Aby operacja pozycjonowania zakończyła się pomyślnie, pochodząca pozycja w strumieniu musi znajdować się w kontrolowanej sekwencji.

## <a name="str"></a>strstreambuf:: str

Wywołania [zawieszają](#freeze)się, a następnie zwracają wskaźnik do początku kontrolowanej sekwencji.

```cpp
char *str();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do początku kontrolowanej sekwencji.

### <a name="remarks"></a>Uwagi

Nie istnieje żaden element kończący null, chyba że zostanie jawnie wstawiony.

### <a name="example"></a>Przykład

Zobacz [strstreambuf::](#freeze) Zablokuj, aby uzyskać przykład, który używa **str**.

## <a name="strstreambuf"></a>strstreambuf:: strstreambuf

Konstruuje obiekt typu `strstreambuf`.

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
Funkcja używana do przydzielania pamięci buforu.

*liczbą*\
Określa długość buforu wskazywanego przez *_Getptr*. Jeśli *_Getptr* nie jest argumentem (pierwszy formularz konstruktora), sugerowanym rozmiarem alokacji dla buforów.

*_Freefunc*\
Funkcja używana do zwolnienia pamięci buforu.

*_Getptr*\
Bufor używany do wprowadzania danych.

*_Putptr*\
Bufor używany do wyprowadzania danych wyjściowych.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor przechowuje wskaźnik o wartości null we wszystkich wskaźnikach kontrolujących bufor wejściowy, bufor wyjściowy i alokację strstreambuf. Ustawia tryb przechowywania strstreambuf, aby kontrolowane sekwencje były modyfikowane i rozszerzalne. Przyjmuje również *liczbę* jako sugerowany rozmiar początkowy alokacji.

Drugi Konstruktor zachowuje się jak pierwszy, z tą różnicą, że przechowuje  *\_Allocfunc* jako wskaźnik do funkcji, aby wywołać przydzielenie magazynu i  *\_Freefunc* jako wskaźnik do funkcji, aby wywołać, aby zwolnić ten magazyn.

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

zachowuje się również jak pierwszy, z wyjątkiem `_Getptr` tego, że określa obiekt Array używany do przechowywania kontrolowanej sekwencji. (W związku z tym nie może być pustym wskaźnikiem). Liczba elementów *N* w tablicy jest określana w następujący sposób:

- Jeśli (`count` > 0), oznacza to N `count`.

- Jeśli (`count` = = 0), to *N* jest `strlen`(( **const** `char` *) `_Getptr` ).

- Jeśli (`count` < 0), to *N* jest **INT_MAX**.

Jeśli `_Putptr` jest wskaźnikiem typu null, funkcja ustanowi tylko bufor wejściowy, wykonując:

```cpp
setg(_Getptr,
    _Getptr,
    _Getptr + N);
```

W przeciwnym razie tworzy zarówno bufory wejściowe, jak i wyjściowe, wykonując:

```cpp
setg(_Getptr,
    _Getptr,
    _Putptr);

setp(_Putptr,
    _Getptr + N);
```

`_Putptr` W tym przypadku musi zawierać się w przedziale `_Getptr`[ `_Getptr`,  +  *N*].

Na koniec trzy konstruktory:

```cpp
strstreambuf(const char *_Getptr,
    streamsize count);

strstreambuf(const signed char *_Getptr,
    streamsize count);

strstreambuf(const unsigned char *_Getptr,
    streamsize count);
```

wszystko działa tak samo jak:

```cpp
streambuf((char *)_Getptr, count);
```

z tą różnicą, że tryb przechowywania sprawia, że kontrolowana sekwencja nie jest modyfikowalna ani rozszerzona.

## <a name="underflow"></a>strstreambuf:: nadmiarowy

Chroniona funkcja wirtualna do wyodrębnienia bieżącego elementu ze strumienia wejściowego.

```cpp
virtual int underflow();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może się powieść `EOF`, zwraca wartość. W przeciwnym razie zwraca bieżący element w strumieniu wejściowym, przekonwertowany zgodnie z powyższym opisem.

### <a name="remarks"></a>Uwagi

Chroniona funkcja wirtualna elementu członkowskiego przedsięwzięciach do wyodrębnienia `ch` bieżącego elementu z bufora wejściowego, a następnie przechodzenia do bieżącego położenia strumienia i zwracania`int`elementu jako`unsigned char`() () **ch**. Można to zrobić tylko w jeden sposób: Jeśli pozycja odczytu jest dostępna, przyjmuje `ch` się jako element zapisany w pozycji odczytu i przesuwa następny wskaźnik dla buforu wejściowego.

## <a name="see-also"></a>Zobacz także

[streambuf](../standard-library/streambuf-typedefs.md#streambuf)\
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
