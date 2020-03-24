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
ms.openlocfilehash: 9b4492f10e2871792d8e1870fcfea37775dc7bde
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150852"
---
# <a name="basic_filebuf-class"></a>basic_filebuf — Klasa

Opisuje bufor strumienia, który kontroluje przekazywanie elementów typu *Char_T*, których cechy znakowe są określane przez klasę *TR*, do i z sekwencji elementów przechowywanych w zewnętrznym pliku.

## <a name="syntax"></a>Składnia

```cpp
template <class Char_T, class Tr = char_traits<Char_T>>
class basic_filebuf : public basic_streambuf<Char_T, Tr>
```

### <a name="parameters"></a>Parametry

*Char_T*\
Podstawowy element buforu pliku.

\ *TR*
Cechy podstawowego elementu buforu plików (zwykle `char_traits<Char_T>`).

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje bufor strumienia, który kontroluje przekazywanie elementów typu *Char_T*, których cechy znakowe są określane przez klasę *TR*, do i z sekwencji elementów przechowywanych w zewnętrznym pliku.

> [!NOTE]
> Obiekty typu `basic_filebuf` są tworzone z wewnętrznym buforem typu __char\*__ niezależnie od `char_type` określonego przez parametr typu *Char_T*. Oznacza to, że ciąg Unicode (zawierający **wchar_t** znaków) zostanie przekonwertowany na ciąg ANSI (zawierający znaki **char** ) przed zapisaniem w buforze wewnętrznym. Aby przechowywać ciągi Unicode w buforze, należy utworzyć nowy bufor typu **wchar_t** i ustawić go przy użyciu metody [`basic_streambuf::pubsetbuf`](../standard-library/basic-streambuf-class.md#pubsetbuf)`()`. Aby zobaczyć przykład demonstrujący to zachowanie, zobacz poniżej.

Obiekt klasy `basic_filebuf<Char_T, Tr>` przechowuje wskaźnik pliku, który wyznacza obiekt `FILE`, który kontroluje strumień skojarzony z otwartym plikiem. Przechowuje również wskaźniki do dwóch zestawów reguł konwersji plików do użycia przez [przepełnienie](#overflow) i [niedomiar](#underflow)chronionych elementów członkowskich. Aby uzyskać więcej informacji, zobacz [`basic_filebuf::open`](#open).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak wymusić obiekt typu `basic_filebuf<wchar_t>` do przechowywania znaków Unicode w buforze wewnętrznym przez wywołanie metody `pubsetbuf()`.

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
|[basic_filebuf](#basic_filebuf)|Konstruuje obiekt typu `basic_filebuf`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Kojarzy nazwę typu z parametrem szablonu `Char_T`.|
|[int_type](#int_type)|Sprawia, że ten typ w zakresie `basic_filebuf`jest równy typowi o tej samej nazwie w zakresie `Tr`.|
|[off_type](#off_type)|Sprawia, że ten typ w zakresie `basic_filebuf`jest równy typowi o tej samej nazwie w zakresie `Tr`.|
|[pos_type](#pos_type)|Sprawia, że ten typ w zakresie `basic_filebuf`jest równy typowi o tej samej nazwie w zakresie `Tr`.|
|[traits_type](#traits_type)|Kojarzy nazwę typu z parametrem szablonu `Tr`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[close](#close)|Zamyka plik.|
|[is_open](#is_open)|Wskazuje, czy plik jest otwarty.|
|[open](#open)|Otwiera plik.|
|[przepływ](#overflow)|Chroniona funkcja wirtualna, która może być wywoływana, gdy nowy znak zostanie wstawiony do pełnego buforu.|
|[pbackfail](#pbackfail)|Chroniona funkcja wirtualna elementu członkowskiego próbuje umieścić element w strumieniu wejściowym, a następnie uczynić go bieżącym elementem (wskazywanym przez następny wskaźnik).|
|[seekoff](#seekoff)|Chroniona funkcja wirtualna elementu członkowskiego próbuje zmienić bieżące położenie dla kontrolowanych strumieni.|
|[seekpos](#seekpos)|Chroniona funkcja wirtualna elementu członkowskiego próbuje zmienić bieżące położenie dla kontrolowanych strumieni.|
|[setbuf](#setbuf)|Chroniona funkcja wirtualna elementu członkowskiego wykonuje operację konkretną dla każdego pochodnego buforu strumienia.|
|[Wymiany](#swap)|Wymienia zawartość tego `basic_filebuf` dla zawartości podanego parametru `basic_filebuf`.|
|[synchronizacji](#sync)|Chroniona funkcja wirtualna próbuje zsynchronizować kontrolowane strumienie ze wszystkimi skojarzonymi strumieniami zewnętrznymi.|
|[uflow](../standard-library/basic-streambuf-class.md#uflow)|Chroniona funkcja wirtualna w celu wyodrębnienia bieżącego elementu ze strumienia wejściowego.|
|[miar](#underflow)|Chroniona funkcja wirtualna w celu wyodrębnienia bieżącego elementu ze strumienia wejściowego.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<fstream — >

**Przestrzeń nazw:** std

## <a name="basic_filebufbasic_filebuf"></a><a name="basic_filebuf"></a>basic_filebuf:: basic_filebuf

Konstruuje obiekt typu `basic_filebuf`.

```cpp
basic_filebuf();

basic_filebuf(basic_filebuf&& right);
```

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor przechowuje wskaźnik o wartości null we wszystkich wskaźnikach kontrolujących bufor wejściowy i bufor wyjściowy. Przechowuje również wskaźnik o wartości null w wskaźniku pliku.

Drugi Konstruktor inicjuje obiekt z zawartością *prawa*, traktowany jako odwołanie rvalue.

## <a name="basic_filebufchar_type"></a><a name="char_type"></a>basic_filebuf:: char_type

Kojarzy nazwę typu z parametrem szablonu `Char_T`.

```cpp
typedef Char_T char_type;
```

## <a name="basic_filebufclose"></a><a name="close"></a>basic_filebuf:: Close

Zamyka plik.

```cpp
basic_filebuf<Char_T, Tr> *close();
```

### <a name="return-value"></a>Wartość zwracana

Funkcja członkowska zwraca wskaźnik o wartości null, jeśli wskaźnik pliku jest wskaźnikiem o wartości null.

### <a name="remarks"></a>Uwagi

`fclose(fp)``close` wywołań. Jeśli ta funkcja zwróci wartość różną od zera, funkcja zwraca wskaźnik o wartości null. W przeciwnym razie zwraca **to** , aby wskazać, że plik został pomyślnie zamknięty.

W przypadku strumienia szerokiego, jeśli jakieś wstawienia wystąpiły od momentu otwarcia strumienia lub od momentu ostatniego wywołania `streampos`, funkcja wywołuje [`overflow`](#overflow). Wstawia również wszystkie sekwencje potrzebne do przywrócenia stanu konwersji początkowej przy użyciu aspektu konwersji plików `fac` do wywołania `fac.unshift` zgodnie z wymaganiami. Każdy wygenerowany element `byte` typu **char** jest zapisywana w skojarzonym strumieniu wydzielonym przez wskaźnik pliku `fp` tak jak w przypadku kolejnych wywołań formularza `fputc(byte, fp)`. Jeśli wywołanie `fac.unshift` lub dowolnego zapisu nie powiedzie się, funkcja nie powiedzie się.

### <a name="example"></a>Przykład

W poniższym przykładzie przyjęto założenie, że dwa pliki w bieżącym katalogu: *basic_filebuf_close. txt* (zawartość to "testowanie") i *IOTest. txt* (zawartość to "ssss").

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

## <a name="basic_filebufint_type"></a><a name="int_type"></a>basic_filebuf:: int_type

Sprawia, że ten typ w zakresie `basic_filebuf` jest równoważny z typem o tej samej nazwie w zakresie `Tr`.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="basic_filebufis_open"></a><a name="is_open"></a>basic_filebuf:: is_open

Wskazuje, czy plik jest otwarty.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli wskaźnik pliku nie ma wartości null.

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

## <a name="basic_filebufoff_type"></a><a name="off_type"></a>basic_filebuf:: off_type

Sprawia, że ten typ w zakresie `basic_filebuf` jest równoważny z typem o tej samej nazwie w zakresie `Tr`.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="basic_filebufopen"></a><a name="open"></a>basic_filebuf:: Open

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

*Nazwa pliku*\
Nazwa pliku do otwarcia.

\ *trybu*
Jedno z wyliczeń w [`ios_base::openmode`](../standard-library/ios-base-class.md#openmode).

\ *ochrony*
Domyślna ochrona otwierania plików, równoważna parametrowi *Shflag* w [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="return-value"></a>Wartość zwracana

Jeśli bufor jest już otwarty lub wskaźnik pliku jest wskaźnikiem typu null, funkcja zwraca wskaźnik o wartości null. W przeciwnym razie zwraca **to**.

### <a name="remarks"></a>Uwagi

Funkcja członkowska otwiera plik o nazwie *filename*, wywołując [`fopen`](../c-runtime-library/reference/fopen-wfopen.md)`(filename, strmode)`. `strmode` jest określana na podstawie `mode & ~(`[`ate`](../standard-library/ios-base-class.md#openmode) `|` [`binary`](../standard-library/ios-base-class.md#openmode)`)`:

- `ios_base::in` zostanie `"r"` (otwiera istniejący plik do odczytu).

- [ios_base:: out](../standard-library/ios-base-class.md#fmtflags) lub `ios_base::out | ios_base::trunc` zostaje `"w"` (Obetnij istniejący plik lub Utwórz do zapisu).

- `ios_base::out | app` zostanie `"a"` (otwiera istniejący plik do dołączania wszystkich zapisów).

- `ios_base::in | ios_base::out` zostanie `"r+"` (otwiera istniejący plik do odczytu i zapisu).

- `ios_base::in | ios_base::out | ios_base::trunc` stać się `"w+"` (obcina istniejący plik lub tworzy do odczytu i zapisu).

- `ios_base::in | ios_base::out | ios_base::app` zostanie `"a+"` (otwiera istniejący plik do odczytu i do dołączania wszystkich zapisów).

Jeśli `mode & ios_base::binary` ma wartość różną od zera, funkcja dołącza `b` do `strmode` otwarcia strumienia binarnego zamiast strumienia tekstu. Następnie przechowuje wartość zwracaną przez `fopen` w `fp`wskaźnika pliku. Jeśli `mode & ios_base::ate` jest różna od zera, a wskaźnik pliku nie jest wskaźnikiem null, funkcja wywołuje `fseek(fp, 0, SEEK_END)`, aby umieścić strumień na końcu pliku. Jeśli operacja pozycjonowania nie powiedzie się, funkcja wywołuje [`close`](#close)`(fp)` i zapisuje wskaźnik o wartości null w wskaźniku pliku.

Jeśli wskaźnik pliku nie jest pustym wskaźnikiem, funkcja określa zestaw reguł konwersji plików: `use_facet<codecvt<Char_T, char, traits_type::`[`state_type`](../standard-library/char-traits-struct.md#state_type)`> >(`[`getloc`](../standard-library/basic-streambuf-class.md#getloc)`)`, do użycia przez [nadmiarowy](#underflow) i [przepełnienie](#overflow).

Jeśli wskaźnik pliku jest wskaźnikiem typu null, funkcja zwraca wskaźnik o wartości null. W przeciwnym razie zwraca **to**.

### <a name="example"></a>Przykład

Zobacz [`basic_filebuf::close`](#close) , aby zapoznać się z przykładem, który używa `open`.

## <a name="basic_filebufoperator"></a><a name="op_eq"></a>basic_filebuf:: operator =

Przypisz zawartość tego obiektu buforu strumienia. Jest to przypisanie przenoszenia obejmujące rvalue, które nie pozostawia kopii w tle.

```cpp
basic_filebuf& operator=(basic_filebuf&& right);
```

### <a name="parameters"></a>Parametry

*prawa*\
Odwołanie rvalue do obiektu [basic_filebuf](../standard-library/basic-filebuf-class.md) .

### <a name="return-value"></a>Wartość zwracana

Zwraca __* this__.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zastępuje zawartość obiektu przy użyciu zawartości *Right*, traktowanej jako odwołanie rvalue. Aby uzyskać więcej informacji, zobacz [rvalue Reference deklarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="basic_filebufoverflow"></a><a name="overflow"></a>basic_filebuf:: overflow

Wywoływana, gdy nowy znak zostanie wstawiony do pełnego buforu.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak, który ma zostać wstawiony do buforu lub `traits_type::eof`.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może się powieść, zwraca `traits_type::eof`. W przeciwnym razie zwraca `traits_type::`[`not_eof`](../standard-library/char-traits-struct.md#not_eof)`(_Meta)`.

### <a name="remarks"></a>Uwagi

Jeśli `_Meta != traits_type::`[`eof`](../standard-library/char-traits-struct.md#eof), chroniona funkcja wirtualna elementu członkowskiego próbuje wstawić element `ch = traits_type::`[`to_char_type`](../standard-library/char-traits-struct.md#to_char_type)`(_Meta)` do buforu wyjściowego. Można to zrobić na różne sposoby:

- Jeśli dostępna jest pozycja zapisu, może ona przechowywać element w pozycji zapisu i zwiększać następny wskaźnik dla buforu wyjściowego.

- Możliwe jest udostępnienie pozycji zapisu przez przydzielenie nowego lub dodatkowego magazynu dla buforu danych wyjściowych.

- Można skonwertować wszystkie oczekujące dane wyjściowe w buforze wyjściowym, po którym następuje `ch`, przy użyciu aspektu konwersji plików `fac` do wywołania `fac.out` zgodnie z wymaganiami. Każdy wygenerowany element `ch` typu *char* jest zapisywana w skojarzonym strumieniu wydzielonym przez wskaźnik pliku `fp` tak jak w przypadku kolejnych wywołań formularza `fputc(ch, fp)`. Jeśli jakakolwiek konwersja lub zapis nie powiedzie się, funkcja nie powiedzie się.

## <a name="basic_filebufpbackfail"></a><a name="pbackfail"></a>basic_filebuf::p nie powiodło się

Próbuje umieścić element w strumieniu wejściowym, a następnie uczynić go bieżącym elementem (wskazywanym przez następny wskaźnik).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak, który ma zostać wstawiony do buforu lub `traits_type::eof`.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może się powieść, zwraca `traits_type::eof`. W przeciwnym razie zwraca `traits_type::`[`not_eof`](../standard-library/char-traits-struct.md#not_eof)`(_Meta)`.

### <a name="remarks"></a>Uwagi

Chroniona funkcja wirtualna elementu członkowskiego umieszcza element w buforze wejściowym, a następnie ustawia go jako bieżący element (wskazywany przez następny wskaźnik). Jeśli `_Meta == traits_type::`[`eof`](../standard-library/char-traits-struct.md#eof), element, który ma zostać wypchnięci z powrotem, jest efektywnie tym, który znajduje się już w strumieniu przed bieżącym elementem. W przeciwnym razie ten element jest zastępowany przez `ch = traits_type::`[`to_char_type`](../standard-library/char-traits-struct.md#to_char_type)`(_Meta)`. Funkcja może umieścić element na różne sposoby:

- Jeśli pozycja `putback` jest dostępna, a element przechowywany porównuje równe `ch`, może zmniejszyć następny wskaźnik dla buforu wejściowego.

- Jeśli funkcja może zapewnić dostępność `putback` pozycji, można to zrobić, ustawić następny wskaźnik, aby wskazywał na tę pozycję, i przechowywać `ch` w tym miejscu.

- Jeśli funkcja może wypchnąć element do strumienia wejściowego, może to zrobić, na przykład przez wywołanie `ungetc` dla elementu typu **char**.

## <a name="basic_filebufpos_type"></a><a name="pos_type"></a>basic_filebuf::p os_type

Sprawia, że ten typ w zakresie `basic_filebuf` jest równoważny z typem o tej samej nazwie w zakresie `Tr`.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="basic_filebufseekoff"></a><a name="seekoff"></a>basic_filebuf:: seekoff

Próbuje zmienić bieżące położenie dla kontrolowanych strumieni.

```cpp
virtual pos_type seekoff(
    off_type _Off,
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

Zwraca nową pozycję lub nieprawidłową pozycję strumienia.

### <a name="remarks"></a>Uwagi

Chroniona funkcja wirtualna elementu członkowskiego próbuje zmienić bieżące położenie dla kontrolowanych strumieni. Dla obiektu klasy [`basic_filebuf`](../standard-library/basic-filebuf-class.md)`<Char_T, Tr>`pozycja strumienia może być reprezentowana przez obiekt typu `fpos_t`, który przechowuje przesunięcie i wszelkie informacje o stanie potrzebne do przeanalizowania strumienia szerokiego. Przesunięcie zero odnosi się do pierwszego elementu strumienia. (Obiekt typu [`pos_type`](../standard-library/basic-streambuf-class.md#pos_type) przechowuje co najmniej obiekt `fpos_t`).

W przypadku pliku otwartego do odczytu i zapisu zarówno strumienie wejściowe, jak i wyjściowe są rozmieszczone wspólnie. Aby przełączać się między wstawianiem i wyodrębnianiem, należy wywołać [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) lub [`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos). Wywołania `pubseekoff` (i w związku z tym `seekoff`) mają różne ograniczenia dotyczące [strumieni tekstu](../c-runtime-library/text-and-binary-streams.md), [strumieni binarnych](../c-runtime-library/text-and-binary-streams.md)i [szerokich strumieni](../c-runtime-library/byte-and-wide-streams.md).

Jeśli wskaźnik pliku `fp` jest wskaźnikiem typu null, funkcja kończy się niepowodzeniem. W przeciwnym razie próbuje zmienić pozycję strumienia, wywołując `fseek(fp, _Off, _Way)`. Jeśli ta funkcja się powiedzie, a wynikiem `fposn` można ustalić przez wywołanie `fgetpos(fp, &fposn)`, funkcja się powiedzie. Jeśli funkcja się powiedzie, zwraca wartość typu `pos_type` zawierającą `fposn`. W przeciwnym razie zwraca nieprawidłową pozycję strumienia.

## <a name="basic_filebufseekpos"></a><a name="seekpos"></a>basic_filebuf:: seekpos

Próbuje zmienić bieżące położenie dla kontrolowanych strumieni.

```cpp
virtual pos_type seekpos(
    pos_type _Sp,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*\
Pozycja do wyszukania.

*_Which*\
Określa tryb dla pozycji wskaźnika. Wartość domyślna to umożliwienie modyfikacji pozycji odczytu i zapisu.

### <a name="return-value"></a>Wartość zwracana

Jeśli wskaźnik pliku `fp` jest wskaźnikiem typu null, funkcja kończy się niepowodzeniem. W przeciwnym razie próbuje zmienić pozycję strumienia, wywołując `fsetpos(fp, &fposn)`, gdzie `fposn` jest obiektem `fpos_t` przechowywanym w `pos`. Jeśli ta funkcja się powiedzie, funkcja zwróci wartość `pos`. W przeciwnym razie zwraca nieprawidłową pozycję strumienia. Aby określić, czy pozycja strumienia jest nieprawidłowa, należy porównać wartość zwracaną z `pos_type(off_type(-1))`.

### <a name="remarks"></a>Uwagi

Chroniona funkcja wirtualna elementu członkowskiego próbuje zmienić bieżące położenie dla kontrolowanych strumieni. Dla obiektu klasy [`basic_filebuf`](../standard-library/basic-filebuf-class.md)`<Char_T, Tr>`pozycja strumienia może być reprezentowana przez obiekt typu `fpos_t`, który przechowuje przesunięcie i wszelkie informacje o stanie potrzebne do przeanalizowania strumienia szerokiego. Przesunięcie zero odnosi się do pierwszego elementu strumienia. (Obiekt typu `pos_type` przechowuje co najmniej obiekt `fpos_t`).

W przypadku pliku otwartego do odczytu i zapisu zarówno strumienie wejściowe, jak i wyjściowe są rozmieszczone wspólnie. Aby przełączać się między wstawianiem i wyodrębnianiem, należy wywołać [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) lub [`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos). Wywołania `pubseekoff` (i do `seekoff`) mają różne ograniczenia dotyczące strumieni tekstu, strumieni binarnych i szerokich strumieni.

W przypadku strumienia szerokiego, jeśli jakieś wstawienia wystąpiły od momentu otwarcia strumienia lub od czasu ostatniego wywołania do `streampos`, funkcja wywołuje [przepełnienie](#overflow). Wstawia również wszystkie sekwencje potrzebne do przywrócenia stanu konwersji początkowej przy użyciu aspektu konwersji plików `fac` do wywołania `fac.unshift` zgodnie z wymaganiami. Każdy wygenerowany element `byte` typu **char** jest zapisywana w skojarzonym strumieniu wydzielonym przez wskaźnik pliku `fp` tak jak w przypadku kolejnych wywołań formularza `fputc(byte, fp)`. Jeśli wywołanie `fac.unshift` lub dowolnego zapisu nie powiedzie się, funkcja nie powiedzie się.

## <a name="basic_filebufsetbuf"></a><a name="setbuf"></a>basic_filebuf:: setbuf

Wykonuje operację konkretną dla każdego pochodnego buforu strumienia.

```cpp
virtual basic_streambuf<Char_T, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*_Buffer*\
Wskaźnik do buforu.

*liczba*\
Rozmiar buforu.

### <a name="return-value"></a>Wartość zwracana

Funkcja chronionej składowej zwraca zero, jeśli wskaźnik pliku `fp` jest wskaźnikiem o wartości null.

### <a name="remarks"></a>Uwagi

`setbuf` wywołań `setvbuf( fp, (char*) _Buffer, _IOFBF, count * sizeof( Char_T))`, aby zaoferować tablicę elementów `count`, zaczynając od *_Buffer* jako bufor strumienia. Jeśli ta funkcja zwróci wartość różną od zera, funkcja zwraca wskaźnik o wartości null. W przeciwnym razie zwraca **to** do sukcesu.

## <a name="basic_filebufswap"></a><a name="swap"></a>basic_filebuf:: swap

Wymienia zawartość tego `basic_filebuf` dla zawartości podanej `basic_filebuf`.

```cpp
void swap(basic_filebuf& right);
```

### <a name="parameters"></a>Parametry

*prawa*\
Odwołanie lvalue do innego `basic_filebuf`.

## <a name="basic_filebufsync"></a><a name="sync"></a>basic_filebuf:: Sync

Próbuje zsynchronizować kontrolowane strumienie ze wszystkimi skojarzonymi strumieniami zewnętrznymi.

```cpp
virtual int sync();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca zero, jeśli wskaźnik pliku `fp` jest wskaźnikiem o wartości null. W przeciwnym razie zwraca zero tylko wtedy, gdy wywołania zarówno [przepełnienia](#overflow) , jak i `fflush(fp)` pomyślne w wyniku opróżniania wszystkich oczekujących danych wyjściowych do strumienia.

## <a name="basic_filebuftraits_type"></a><a name="traits_type"></a>basic_filebuf:: traits_type

Kojarzy nazwę typu z parametrem szablonu `Tr`.

```cpp
typedef Tr traits_type;
```

## <a name="basic_filebufunderflow"></a><a name="underflow"></a>basic_filebuf:: niedopełnienie

Wyodrębnia bieżący element ze strumienia wejściowego.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może się powieść, zwraca `traits_type::`[`eof`](../standard-library/char-traits-struct.md#eof). W przeciwnym razie zwraca `ch`, przekonwertowane zgodnie z opisem w sekcji uwagi.

### <a name="remarks"></a>Uwagi

Chroniona funkcja wirtualna elementu członkowskiego próbuje wyodrębnić bieżący element `ch` ze strumienia wejściowego i zwrócić element jako `traits_type::`[`to_int_type`](../standard-library/char-traits-struct.md#to_int_type)`(ch)`. Można to zrobić na różne sposoby:

- Jeśli dostępna jest pozycja odczytu, przyjmuje `ch` jako element zapisany w pozycji odczytu i postępuje zgodnie z kolejnymi wskaźnikami dla buforu wejściowego.

- Może odczytać jeden lub więcej elementów typu **char**, tak jak w przypadku kolejnych wywołań formularza `fgetc(fp)`i przekonwertowania ich do `ch` elementu typu `Char_T` przy użyciu aspektu konwersji plików `fac` do wywołania `fac.in` zgodnie z wymaganiami. W przypadku niepowodzenia odczytu lub konwersji funkcja nie powiedzie się.

## <a name="see-also"></a>Zobacz też

[\<fstream — >](../standard-library/fstream.md)\
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
\ [programowania iostream](../standard-library/iostream-programming.md)
[Konwencje iostream](../standard-library/iostreams-conventions.md)
