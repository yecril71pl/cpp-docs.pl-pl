---
title: basic_filebuf — Klasa
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_filebuf
- fstream/std::basic_filebuf::char_type
- fstream/std::basic_filebuf::int_type
- fstream/std::basic_filebuf::off_type
- fstream/std::basic_filebuf::pos_type
- fstream/std::basic_filebuf::traits_type
- fstream/std::basic_filebuf::close
- fstream/std::basic_filebuf::is_open
- fstream/std::basic_filebuf::open
- fstream/std::basic_filebuf::overflow
- fstream/std::basic_filebuf::pbackfail
- fstream/std::basic_filebuf::seekoff
- fstream/std::basic_filebuf::seekpos
- fstream/std::basic_filebuf::setbuf
- fstream/std::basic_filebuf::Swap
- fstream/std::basic_filebuf::sync
- fstream/std::basic_filebuf::uflow
- fstream/std::basic_filebuf::underflow
helpviewer_keywords:
- std::basic_filebuf [C++]
- std::basic_filebuf [C++], char_type
- std::basic_filebuf [C++], int_type
- std::basic_filebuf [C++], off_type
- std::basic_filebuf [C++], pos_type
- std::basic_filebuf [C++], traits_type
- std::basic_filebuf [C++], close
- std::basic_filebuf [C++], is_open
- std::basic_filebuf [C++], open
- std::basic_filebuf [C++], overflow
- std::basic_filebuf [C++], pbackfail
- std::basic_filebuf [C++], seekoff
- std::basic_filebuf [C++], seekpos
- std::basic_filebuf [C++], setbuf
- std::basic_filebuf [C++], Swap
- std::basic_filebuf [C++], sync
- std::basic_filebuf [C++], uflow
- std::basic_filebuf [C++], underflow
ms.assetid: 3196ba5c-bf38-41bd-9a95-70323ddfca1a
ms.openlocfilehash: 35bed08f2495c971df7f79f62e32b3ff68dfb3d2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376879"
---
# <a name="basic_filebuf-class"></a>basic_filebuf — Klasa

Opisuje bufor strumienia, który steruje transmisją elementów typu *Char_T*, których cechy charakteru są określane przez klasę *Tr*, do i z sekwencji elementów przechowywanych w pliku zewnętrznym.

## <a name="syntax"></a>Składnia

```cpp
template <class Char_T, class Tr = char_traits<Char_T>>
class basic_filebuf : public basic_streambuf<Char_T, Tr>
```

### <a name="parameters"></a>Parametry

*Char_T*\
Podstawowy element buforu plików.

*Tr*\
Cechy podstawowego elementu buforu plików (zwykle `char_traits<Char_T>`).

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje bufor strumienia, który steruje transmisją elementów typu *Char_T*, których cechy charakteru są określane przez klasę *Tr*, do i z sekwencji elementów przechowywanych w pliku zewnętrznym.

> [!NOTE]
> Obiekty typu `basic_filebuf` są tworzone z wewnętrznym buforem typu `char_type` __char,\* __ niezależnie od określonego przez parametr typu *Char_T*. Oznacza to, że ciąg Unicode (zawierający **wchar_t** znaków) zostanie przekonwertowany na ciąg ANSI (zawierający znaki **char)** przed zapisaniem go w buforze wewnętrznym. Aby przechowywać ciągi Unicode w buforze, należy utworzyć nowy bufor [`basic_streambuf::pubsetbuf`](../standard-library/basic-streambuf-class.md#pubsetbuf) `()` typu **wchar_t** i ustawić go przy użyciu metody. Aby zobaczyć przykład, który pokazuje to zachowanie, zobacz poniżej.

Obiekt klasy `basic_filebuf<Char_T, Tr>` przechowuje wskaźnik pliku, który `FILE` wyznacza obiekt, który steruje strumieniem skojarzonym z otwartym plikiem. Przechowuje również wskaźniki do dwóch aspektów konwersji plików do użytku przez chronione funkcje członkowskie [przepełnienie](#overflow) i [niedopełnienie](#underflow). Aby uzyskać więcej [`basic_filebuf::open`](#open)informacji, zobacz .

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `basic_filebuf<wchar_t>` wymusić obiekt typu do przechowywania `pubsetbuf()` znaków Unicode w buforze wewnętrznym, wywołując metodę.

```cpp
// unicode_basic_filebuf.cpp
// compile with: /EHsc

#include <iostream>
#include <string>
#include <fstream>
#include <iomanip>
#include <memory.h>
#include <string.h>

#define IBUFSIZE 16

using namespace std;

void hexdump(const string& filename);

int main()
{
    wchar_t* wszHello = L"Hello World";
    wchar_t wBuffer[128];

    basic_filebuf<wchar_t> wOutFile;

    // Open a file, wcHello.txt, then write to it, then dump the
    // file's contents in hex
    wOutFile.open("wcHello.txt",
        ios_base::out | ios_base::trunc | ios_base::binary);
    if(!wOutFile.is_open())
    {
        cout << "Error Opening wcHello.txt\n";
        return -1;
    }
    wOutFile.sputn(wszHello, (streamsize)wcslen(wszHello));
    wOutFile.close();
    cout << "Hex Dump of wcHello.txt - note that output is ANSI chars:\n";
    hexdump(string("wcHello.txt"));

    // Open a file, wwHello.txt, then set the internal buffer of
    // the basic_filebuf object to be of type wchar_t, then write
    // to the file and dump the file's contents in hex
    wOutFile.open("wwHello.txt",
        ios_base::out | ios_base::trunc | ios_base::binary);
    if(!wOutFile.is_open())
    {
        cout << "Error Opening wwHello.txt\n";
        return -1;
    }
    wOutFile.pubsetbuf(wBuffer, (streamsize)128);
    wOutFile.sputn(wszHello, (streamsize)wcslen(wszHello));
    wOutFile.close();
    cout << "\nHex Dump of wwHello.txt - note that output is wchar_t chars:\n";
    hexdump(string("wwHello.txt"));

    return 0;
}

// dump contents of filename to stdout in hex
void hexdump(const string& filename)
{
    fstream ifile(filename.c_str(),
        ios_base::in | ios_base::binary);
    char *ibuff = new char[IBUFSIZE];
    char *obuff = new char[(IBUFSIZE*2)+1];
    int i;

    if(!ifile.is_open())
    {
        cout << "Cannot Open " << filename.c_str()
             << " for reading\n";
        return;
    }
    if(!ibuff || !obuff)
    {
        cout << "Cannot Allocate buffers\n";
        ifile.close();
        return;
    }

    while(!ifile.eof())
    {
        memset(obuff,0,(IBUFSIZE*2)+1);
        memset(ibuff,0,IBUFSIZE);
        ifile.read(ibuff,IBUFSIZE);

        // corner case where file is exactly a multiple of
        // 16 bytes in length
        if(ibuff[0] == 0 && ifile.eof())
            break;

        for(i = 0; i < IBUFSIZE; i++)
        {
            if(ibuff[i] >= ' ')
                obuff[i] = ibuff[i];
            else
                obuff[i] = '.';

            cout << setfill('0') << setw(2) << hex
                 << (int)ibuff[i] << ' ';
        }
        cout << "  " << obuff << endl;
    }
    ifile.close();
}
```

```Output
Hex Dump of wcHello.txt - note that output is ANSI chars:
48 65 6c 6c 6f 20 57 6f 72 6c 64 00 00 00 00 00   Hello World.....

Hex Dump of wwHello.txt - note that output is wchar_t chars:
48 00 65 00 6c 00 6c 00 6f 00 20 00 57 00 6f 00   H.e.l.l.o. .W.o.
72 00 6c 00 64 00 00 00 00 00 00 00 00 00 00 00   r.l.d...........
```

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Basic_filebuf](#basic_filebuf)|Konstruuje obiekt `basic_filebuf`typu .|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[Char_type](#char_type)|Kojarzy nazwę typu `Char_T` z parametrem szablonu.|
|[Int_type](#int_type)|Sprawia, że `basic_filebuf`ten typ w zakresie 's równoważne typ o tej samej nazwie w `Tr` zakresie.|
|[off_type](#off_type)|Sprawia, że `basic_filebuf`ten typ w zakresie 's równoważne typ o tej samej nazwie w `Tr` zakresie.|
|[pos_type](#pos_type)|Sprawia, że `basic_filebuf`ten typ w zakresie 's równoważne typ o tej samej nazwie w `Tr` zakresie.|
|[traits_type](#traits_type)|Kojarzy nazwę typu `Tr` z parametrem szablonu.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Zamknij](#close)|Zamyka plik.|
|[is_open](#is_open)|Wskazuje, czy plik jest otwarty.|
|[Otwórz](#open)|Otwiera plik.|
|[Przepełnienie](#overflow)|Chroniona funkcja wirtualna, która może być wywoływana po wstawieniu nowego znaku do pełnego buforu.|
|[pbackfail](#pbackfail)|Funkcja chronionego elementu członkowskiego wirtualnego próbuje umieścić z powrotem element do strumienia wejściowego, a następnie uczynić go bieżącym elementem (wskazywał przez następny wskaźnik).|
|[poszukiwanie](#seekoff)|Funkcja chronionego wirtualnego elementu członkowskiego próbuje zmienić bieżące pozycje dla kontrolowanych strumieni.|
|[seekpos](#seekpos)|Funkcja chronionego wirtualnego elementu członkowskiego próbuje zmienić bieżące pozycje dla kontrolowanych strumieni.|
|[setbuf](#setbuf)|Funkcja chronionego elementu członkowskiego wirtualnego wykonuje operację określoną dla każdego buforu strumienia pochodnego.|
|[Swap](#swap)|Wymienia się jego `basic_filebuf` treść na treść `basic_filebuf` podanego parametru.|
|[synchronizacja](#sync)|Chroniona, wirtualna funkcja próbuje zsynchronizować kontrolowane strumienie z powiązanymi strumieniami zewnętrznymi.|
|[uflow (polski)](../standard-library/basic-streambuf-class.md#uflow)|Chroniona, wirtualna funkcja wyodrębniania bieżącego elementu ze strumienia wejściowego.|
|[Niedomiar](#underflow)|Chroniona, wirtualna funkcja wyodrębniania bieżącego elementu ze strumienia wejściowego.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<fstream>

**Przestrzeń nazw:** std

## <a name="basic_filebufbasic_filebuf"></a><a name="basic_filebuf"></a>basic_filebuf::basic_filebuf

Konstruuje obiekt `basic_filebuf`typu .

```cpp
basic_filebuf();

basic_filebuf(basic_filebuf&& right);
```

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor przechowuje wskaźnik null we wszystkich wskaźników sterujących buforu wejściowego i buforu wyjściowego. Przechowuje również wskaźnik null w wskaźniku pliku.

Drugi konstruktor inicjuje obiekt z zawartością *right*, traktowane jako odwołanie rvalue.

## <a name="basic_filebufchar_type"></a><a name="char_type"></a>basic_filebuf::char_type

Kojarzy nazwę typu `Char_T` z parametrem szablonu.

```cpp
typedef Char_T char_type;
```

## <a name="basic_filebufclose"></a><a name="close"></a>basic_filebuf::zamknij

Zamyka plik.

```cpp
basic_filebuf<Char_T, Tr> *close();
```

### <a name="return-value"></a>Wartość zwracana

Funkcja elementu członkowskiego zwraca wskaźnik zerowy, jeśli wskaźnik pliku jest wskaźnikiem zerowym.

### <a name="remarks"></a>Uwagi

`close`połączeń `fclose(fp)`telefonicznych . Jeśli ta funkcja zwraca wartość niezerową, funkcja zwraca wskaźnik zerowy. W przeciwnym razie zwraca **to,** aby wskazać, że plik został pomyślnie zamknięty.

Dla szerokiego strumienia, jeśli wystąpiły jakiekolwiek wstawienia od `streampos`czasu otwarcia [`overflow`](#overflow)strumienia lub od ostatniego wywołania , funkcja wywołuje . Wstawia również dowolną sekwencję potrzebną do przywrócenia początkowego `fac` stanu `fac.unshift` konwersji, używając aspektu konwersji pliku do wywołania zgodnie z potrzebami. Każdy `byte` wyprodukowany element typu **char** jest zapisywany w skojarzonym `fp` strumieniu wyznaczonym przez `fputc(byte, fp)`wskaźnik pliku, tak jakby przez kolejne wywołania formularza . Jeśli wywołanie `fac.unshift` lub zapis nie powiedzie się, funkcja nie powiedzie się.

### <a name="example"></a>Przykład

W poniższym przykładzie przyjęto dwa pliki w bieżącym katalogu: *basic_filebuf_close.txt* (zawartość jest "testowanie") i *iotest.txt* (zawartość jest "ssss").

```cpp
// basic_filebuf_close.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main() {
   using namespace std;
   ifstream file;
   basic_ifstream <wchar_t> wfile;
   char c;
   // Open and close with a basic_filebuf
   file.rdbuf()->open( "basic_filebuf_close.txt", ios::in );
   file >> c;
   cout << c << endl;
   file.rdbuf( )->close( );

   // Open/close directly
   file.open( "iotest.txt" );
   file >> c;
   cout << c << endl;
   file.close( );

   // open a file with a wide character name
   wfile.open( L"iotest.txt" );

   // Open and close a nonexistent with a basic_filebuf
   file.rdbuf()->open( "ziotest.txt", ios::in );
   cout << file.fail() << endl;
   file.rdbuf( )->close( );

   // Open/close directly
   file.open( "ziotest.txt" );
   cout << file.fail() << endl;
   file.close( );
}
```

```Output
t
s
0
1
```

## <a name="basic_filebufint_type"></a><a name="int_type"></a>basic_filebuf::int_type

Sprawia, że `basic_filebuf` ten typ w zakresie równoważne `Tr` typ o tej samej nazwie w zakresie.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="basic_filebufis_open"></a><a name="is_open"></a>basic_filebuf::is_open

Wskazuje, czy plik jest otwarty.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli wskaźnik pliku nie jest null.

### <a name="example"></a>Przykład

```cpp
// basic_filebuf_is_open.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main( )
{
   using namespace std;
   ifstream file;
   cout << boolalpha << file.rdbuf( )->is_open( ) << endl;

   file.open( "basic_filebuf_is_open.cpp" );
   cout << file.rdbuf( )->is_open( ) << endl;
}
```

```Output
false
true
```

## <a name="basic_filebufoff_type"></a><a name="off_type"></a>basic_filebuf::off_type

Sprawia, że `basic_filebuf` ten typ w zakresie równoważne `Tr` typ o tej samej nazwie w zakresie.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="basic_filebufopen"></a><a name="open"></a>basic_filebuf::otwórz

Otwiera plik.

```cpp
basic_filebuf<Char_T, Tr> *open(
    const char* filename,
    ios_base::openmode mode,
    int protection = (int)ios_base::_Openprot);

basic_filebuf<Char_T, Tr> *open(
    const char* filename,
    ios_base::openmode mode);

basic_filebuf<Char_T, Tr> *open(
    const wchar_t* filename,
    ios_base::openmode mode,
    int protection = (int)ios_base::_Openprot);

basic_filebuf<Char_T, Tr> *open(
    const wchar_t* filename,
    ios_base::openmode mode);
```

### <a name="parameters"></a>Parametry

*Pod nazwą*\
Nazwa pliku do otwarcia.

*Tryb*\
Jedno z wyliczenia [`ios_base::openmode`](../standard-library/ios-base-class.md#openmode)w .

*Ochrony*\
Domyślna ochrona przed otwarciem pliku, równoważna parametrowi *shflag* w [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="return-value"></a>Wartość zwracana

Jeśli bufor jest już otwarty lub jeśli wskaźnik pliku jest wskaźnikiem zerowym, funkcja zwraca wskaźnik zerowy. W przeciwnym razie zwraca **to**.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego otwiera plik z nazwą [`fopen`](../c-runtime-library/reference/fopen-wfopen.md) `(filename, strmode)` *filename*, wywołując . `strmode`określa się `mode & ~(` [`ate`](../standard-library/ios-base-class.md#openmode) `|` [`binary`](../standard-library/ios-base-class.md#openmode) `)`na podstawie:

- `ios_base::in`(otwórz `"r"` istniejący plik do odczytu).

- [ios_base::out](../standard-library/ios-base-class.md#fmtflags) lub `ios_base::out | ios_base::trunc` staje `"w"` się (obcięć istniejący plik lub utworzyć do zapisu).

- `ios_base::out | app`(otwórz `"a"` istniejący plik do dołączania wszystkich zapisów).

- `ios_base::in | ios_base::out`(otwórz `"r+"` istniejący plik do odczytu i zapisu).

- `ios_base::in | ios_base::out | ios_base::trunc`(obcięć `"w+"` istniejący plik lub utworzyć do odczytu i zapisu).

- `ios_base::in | ios_base::out | ios_base::app`(otwórz `"a+"` istniejący plik do odczytu i dołączania wszystkich zapisów).

Jeśli `mode & ios_base::binary` jest niezerowy, funkcja `b` dołącza `strmode` do otwarcia strumienia binarnego zamiast strumienia tekstu. Następnie przechowuje wartość `fopen` zwróconą w `fp`wskaźniku pliku . Jeśli `mode & ios_base::ate` wskaźnik pliku nie jest wartością zerową, funkcja `fseek(fp, 0, SEEK_END)` wywołuje umieszczenie strumienia na końcu pliku. Jeśli ta operacja pozycjonowania nie powiedzie się, funkcja wywołuje [`close`](#close) `(fp)` i przechowuje wskaźnik null w wskaźniku pliku.

Jeśli wskaźnik pliku nie jest wskaźnikiem zerowym, funkcja określa `use_facet<codecvt<Char_T, char, traits_type::` [`state_type`](../standard-library/char-traits-struct.md#state_type) `> >(` [`getloc`](../standard-library/basic-streambuf-class.md#getloc) `)`aspekt konwersji pliku: , do użycia przez [niedopełnienie](#underflow) i [przepełnienie](#overflow).

Jeśli wskaźnik pliku jest wskaźnikiem zerowym, funkcja zwraca wskaźnik zerowy. W przeciwnym razie zwraca **to**.

### <a name="example"></a>Przykład

Zobacz [`basic_filebuf::close`](#close) przykład, który `open`używa .

## <a name="basic_filebufoperator"></a><a name="op_eq"></a>basic_filebuf::operator=

Przypisz zawartość tego obiektu buforu strumienia. Jest to przypisanie przenoszenia obejmujące wartość rvalue, która nie pozostawia kopii za sobą.

```cpp
basic_filebuf& operator=(basic_filebuf&& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Odwołanie do rvalue do [obiektu basic_filebuf.](../standard-library/basic-filebuf-class.md)

### <a name="return-value"></a>Wartość zwracana

Zwraca __*this__.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zastępuje zawartość obiektu przy użyciu zawartości *prawa,* traktowane jako odwołanie rvalue. Aby uzyskać więcej informacji, zobacz [Rvalue reference declarator: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="basic_filebufoverflow"></a><a name="overflow"></a>basic_filebuf::przepełnienie

Wywoływane, gdy nowy znak jest wstawiany do pełnego buforu.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak, który ma być `traits_type::eof`wstawiany do buforu lub .

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może się `traits_type::eof`powieść, zwraca . W przeciwnym `traits_type::` [`not_eof`](../standard-library/char-traits-struct.md#not_eof) `(_Meta)`razie zwraca .

### <a name="remarks"></a>Uwagi

Jeśli `_Meta != traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof)funkcja chronionego elementu członkowskiego wirtualnego `ch = traits_type::` [`to_char_type`](../standard-library/char-traits-struct.md#to_char_type) `(_Meta)` próbuje wstawić element do buforu wyjściowego. Może to zrobić na różne sposoby:

- Jeśli pozycja zapisu jest dostępna, może przechowywać element w pozycji zapisu i zwiększać następny wskaźnik dla buforu wyjściowego.

- Może udostępnić pozycję zapisu, przydzielając nowe lub dodatkowe miejsce do magazynowania buforu wyjściowego.

- Można przekonwertować wszystkie oczekujące dane `ch`wyjściowe w buforze wyjściowym, a następnie , używając aspektu `fac` konwersji pliku do wywołania `fac.out` w razie potrzeby. Każdy `ch` wyprodukowany element typu *char* jest zapisywany w skojarzonym `fp` strumieniu wyznaczonym przez `fputc(ch, fp)`wskaźnik pliku, tak jakby przez kolejne wywołania formularza . Jeśli konwersja lub zapis nie powiedzie się, funkcja nie powiedzie się.

## <a name="basic_filebufpbackfail"></a><a name="pbackfail"></a>basic_filebuf::pbackfail

Próbuje umieścić z powrotem element do strumienia wejściowego, a następnie uczynić go bieżącym elementem (wskazywowane przez następny wskaźnik).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak, który ma być `traits_type::eof`wstawiany do buforu lub .

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może się `traits_type::eof`powieść, zwraca . W przeciwnym `traits_type::` [`not_eof`](../standard-library/char-traits-struct.md#not_eof) `(_Meta)`razie zwraca .

### <a name="remarks"></a>Uwagi

Funkcja chronionego elementu członkowskiego wirtualnego oddaje element do buforu wejściowego, a następnie sprawia, że jest to bieżący element (wskazywał przez następny wskaźnik). Jeśli `_Meta == traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof)element do odepchnięcia jest skutecznie ten, który jest już w strumieniu przed bieżącym elementem. W przeciwnym razie ten `ch = traits_type::` [`to_char_type`](../standard-library/char-traits-struct.md#to_char_type) `(_Meta)`element zostanie zastąpiony przez . Funkcja może umieścić z powrotem element na różne sposoby:

- Jeśli `putback` pozycja jest dostępna, a element tam `ch`przechowywany porównuje się równa , może zniegować następny wskaźnik dla buforu wejściowego.

- Jeśli funkcja może `putback` udostępnić pozycję, może to zrobić, ustawić następny wskaźnik, `ch` aby wskazać w tej pozycji i przechowywać w tej pozycji.

- Jeśli funkcja może wypchnąć element do strumienia wejściowego, może `ungetc` to zrobić, na przykład wywołując element **typu char**.

## <a name="basic_filebufpos_type"></a><a name="pos_type"></a>basic_filebuf::p_type

Sprawia, że `basic_filebuf` ten typ w zakresie równoważne `Tr` typ o tej samej nazwie w zakresie.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="basic_filebufseekoff"></a><a name="seekoff"></a>basic_filebuf::seekoff

Próbuje zmienić bieżące pozycje dla strumieni kontrolowanych.

```cpp
virtual pos_type seekoff(
    off_type _Off,
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

Zwraca nową pozycję lub nieprawidłową pozycję strumienia.

### <a name="remarks"></a>Uwagi

Funkcja chronionego elementu członkowskiego wirtualnego próbuje zmienić bieżące pozycje dla kontrolowanych strumieni. Dla obiektu klasy [`basic_filebuf`](../standard-library/basic-filebuf-class.md) `<Char_T, Tr>`pozycja strumienia może być reprezentowana `fpos_t`przez obiekt typu , który przechowuje przesunięcie i wszelkie informacje o stanie potrzebne do analizowania szerokiego strumienia. Offset zero odnosi się do pierwszego elementu strumienia. (Obiekt typu [`pos_type`](../standard-library/basic-streambuf-class.md#pos_type) przechowuje co `fpos_t` najmniej obiekt).

W przypadku pliku otwartego zarówno do odczytu, jak i zapisu, strumienie wejściowe i wyjściowe są umieszczone w tandemie. Aby przełączać się między wstawianiem [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) [`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos)i wyodrębnianiem, należy wywołać albo lub . Wywołania `pubseekoff` (a `seekoff`tym samym) mają różne ograniczenia dla [strumieni tekstowych,](../c-runtime-library/text-and-binary-streams.md) [strumieni binarnych](../c-runtime-library/text-and-binary-streams.md)i [szerokich strumieni.](../c-runtime-library/byte-and-wide-streams.md)

Jeśli wskaźnik `fp` pliku jest wskaźnikiem zerowym, funkcja nie powiedzie się. W przeciwnym razie próbuje zmienić `fseek(fp, _Off, _Way)`pozycję strumienia, wywołując . Jeśli ta funkcja powiedzie się, a wynikowa pozycja `fposn` może być określona przez wywołanie, `fgetpos(fp, &fposn)`funkcja powiedzie się. Jeśli funkcja powiedzie się, zwraca `pos_type` wartość `fposn`typu zawierającą . W przeciwnym razie zwraca nieprawidłową pozycję strumienia.

## <a name="basic_filebufseekpos"></a><a name="seekpos"></a>basic_filebuf::seekpos

Próbuje zmienić bieżące pozycje dla strumieni kontrolowanych.

```cpp
virtual pos_type seekpos(
    pos_type _Sp,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*\
Stanowisko do poszukiwania.

*_Which*\
Określa tryb położenia wskaźnika. Domyślnie można zmodyfikować pozycje odczytu i zapisu.

### <a name="return-value"></a>Wartość zwracana

Jeśli wskaźnik `fp` pliku jest wskaźnikiem zerowym, funkcja nie powiedzie się. W przeciwnym razie próbuje zmienić `fsetpos(fp, &fposn)`położenie `fposn` strumienia `fpos_t` przez `pos`wywołanie , gdzie jest obiekt przechowywany w . Jeśli ta funkcja powiedzie `pos`się, funkcja zwraca . W przeciwnym razie zwraca nieprawidłową pozycję strumienia. Aby ustalić, czy pozycja strumienia jest `pos_type(off_type(-1))`nieprawidłowa, porównaj wartość zwracaną z programem .

### <a name="remarks"></a>Uwagi

Funkcja chronionego elementu członkowskiego wirtualnego próbuje zmienić bieżące pozycje dla kontrolowanych strumieni. Dla obiektu klasy [`basic_filebuf`](../standard-library/basic-filebuf-class.md) `<Char_T, Tr>`pozycja strumienia może być reprezentowana `fpos_t`przez obiekt typu , który przechowuje przesunięcie i wszelkie informacje o stanie potrzebne do analizowania szerokiego strumienia. Offset zero odnosi się do pierwszego elementu strumienia. (Obiekt typu `pos_type` przechowuje co `fpos_t` najmniej obiekt).

W przypadku pliku otwartego zarówno do odczytu, jak i zapisu, strumienie wejściowe i wyjściowe są umieszczone w tandemie. Aby przełączać się między wstawianiem [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) [`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos)i wyodrębnianiem, należy wywołać albo lub . Wywołania `pubseekoff` (i `seekoff`do) mają różne ograniczenia dla strumieni tekstu, strumieni binarnych i szerokich strumieni.

W przypadku szerokiego strumienia, jeśli od momentu otwarcia strumienia wystąpiły jakiekolwiek wstawienia lub od ostatniego wywołania `streampos`funkcji, funkcja wywołuje [przepełnienie](#overflow). Wstawia również dowolną sekwencję potrzebną do przywrócenia początkowego `fac` stanu `fac.unshift` konwersji, używając aspektu konwersji pliku do wywołania zgodnie z potrzebami. Każdy `byte` wyprodukowany element typu **char** jest zapisywany w skojarzonym `fp` strumieniu wyznaczonym przez `fputc(byte, fp)`wskaźnik pliku, tak jakby przez kolejne wywołania formularza . Jeśli wywołanie `fac.unshift` lub zapis nie powiedzie się, funkcja nie powiedzie się.

## <a name="basic_filebufsetbuf"></a><a name="setbuf"></a>basic_filebuf::setbuf

Wykonuje operację określoną dla każdego buforu strumienia pochodnego.

```cpp
virtual basic_streambuf<Char_T, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*_Buffer*\
Wskaźnik do buforu.

*Liczba*\
Rozmiar buforu.

### <a name="return-value"></a>Wartość zwracana

Funkcja chronionego elementu członkowskiego zwraca `fp` wartość zero, jeśli wskaźnik pliku jest wskaźnikiem zerowym.

### <a name="remarks"></a>Uwagi

`setbuf`wywołania `setvbuf( fp, (char*) _Buffer, _IOFBF, count * sizeof( Char_T))` do zaoferowania `count` tablicy elementów, począwszy od *_Buffer* jako bufor dla strumienia. Jeśli ta funkcja zwraca wartość niezerową, funkcja zwraca wskaźnik zerowy. W przeciwnym razie zwraca **to,** aby zasygnalizować sukces.

## <a name="basic_filebufswap"></a><a name="swap"></a>basic_filebuf::swap

Wymienia zawartość tego `basic_filebuf` na zawartość dostarczonego `basic_filebuf`.

```cpp
void swap(basic_filebuf& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Lvalue odniesienie do `basic_filebuf`innego .

## <a name="basic_filebufsync"></a><a name="sync"></a>basic_filebuf::synchronizacja

Próbuje zsynchronizować kontrolowane strumienie z wszystkich skojarzonych strumieni zewnętrznych.

```cpp
virtual int sync();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość zero, `fp` jeśli wskaźnik pliku jest wskaźnikiem zerowym. W przeciwnym razie zwraca zero tylko wtedy, gdy wywołania [przepełnienia](#overflow) i `fflush(fp)` zakończyć się powodzeniem w opróżnianiu wszelkich oczekujących danych wyjściowych do strumienia.

## <a name="basic_filebuftraits_type"></a><a name="traits_type"></a>basic_filebuf::traits_type

Kojarzy nazwę typu `Tr` z parametrem szablonu.

```cpp
typedef Tr traits_type;
```

## <a name="basic_filebufunderflow"></a><a name="underflow"></a>basic_filebuf::niedopełnienie

Wyodrębnia bieżący element ze strumienia wejściowego.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może się `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof)powieść, zwraca . W przeciwnym `ch`razie zwraca , przekonwertowane zgodnie z opisem w uwagach sekcji.

### <a name="remarks"></a>Uwagi

Funkcja chronionego elementu członkowskiego wirtualnego `ch` próbuje wyodrębnić bieżący element `traits_type::` [`to_int_type`](../standard-library/char-traits-struct.md#to_int_type) `(ch)`ze strumienia wejściowego i zwrócić element jako . Może to zrobić na różne sposoby:

- Jeśli pozycja odczytu jest `ch` dostępna, przyjmuje jako element przechowywany w pozycji odczytu i przesuwa następny wskaźnik dla buforu wejściowego.

- Może odczytać jeden lub więcej elementów **typu char**, `fgetc(fp)`tak jakby przez kolejne `ch` wywołania formularza , i przekonwertować je na element typu `Char_T` za pomocą aspektu `fac` konwersji pliku do wywołania `fac.in` w razie potrzeby. Jeśli odczyt lub konwersja nie powiedzie się, funkcja nie powiedzie się.

## <a name="see-also"></a>Zobacz też

[\<>fstream](../standard-library/fstream.md)\
[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
