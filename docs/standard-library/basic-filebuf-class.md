---
title: basic_filebuf — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ee6c74693987c35f37caf210e604835061cbefd6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715341"
---
# <a name="basicfilebuf-class"></a>basic_filebuf — Klasa

W tym artykule opisano buforu strumieni, który kontroluje transmisji elementów typu *Elem*, którego cech są określane przez klasę *Tr*, do i z sekwencji elementów przechowywanych w pliku zewnętrznym.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_filebuf : public basic_streambuf<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem*<br/>
Podstawowy element buforu plików.

*TR*<br/>
Cechy elementu podstawowego buforu pliku (zazwyczaj `char_traits` <  `Elem`>).

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje buforu strumieni, który kontroluje transmisji elementów typu *Elem*, którego cech są określane przez klasę *Tr*, do i z sekwencji elementów przechowywanych w Plik zewnętrzny.

> [!NOTE]
> Obiekty typu `basic_filebuf` są tworzone przy użyciu buforu wewnętrznego typu `char *` niezależnie od wartości `char_type` określony przez parametr typu *Elem*. Oznacza to, że ciąg Unicode (zawierający **wchar_t** znaków) zostanie przekonwertowany na ciąg ANSI (zawierający **char** znaków) zanim zostaną zapisane do wewnętrznego buforu. Do przechowywania ciągów Unicode w buforze, Utwórz bufor nowego typu **wchar_t** i ustaw ją za pomocą [basic_streambuf::pubsetbuf](../standard-library/basic-streambuf-class.md#pubsetbuf) `()` metody. Aby zobaczyć przykład demonstrujący ten problem, zobacz poniżej.

Obiekt klasy `basic_filebuf` <  `Elem`, `Tr`> przechowuje wskaźnik pliku, który wyznacza `FILE` obiekt, który kontroluje strumienia skojarzone z otwartego pliku. Przechowuje także wskaźniki do dwóch zestawów reguł konwersji plików do użytku przez funkcje składowe chronione [przepełnienie](#overflow) i [niedopełnienie](#underflow). Aby uzyskać więcej informacji, zobacz [basic_filebuf::open](#open).

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób wymusić obiektu typu `basic_filebuf<wchar_t>` do przechowywania znaki Unicode w jego wewnętrznego buforu, wywołując `pubsetbuf()` metody.

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
|[basic_filebuf](#basic_filebuf)|Tworzy obiekt typu `basic_filebuf`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Kojarzy nazwę typu z `Elem` parametru szablonu.|
|[int_type](#int_type)|Sprawia, że tego typu w ramach `basic_filebuf`firmy odpowiednikiem typu o takiej samej nazwie w zakresie `Tr` zakresu.|
|[off_type](#off_type)|Sprawia, że tego typu w ramach `basic_filebuf`firmy odpowiednikiem typu o takiej samej nazwie w zakresie `Tr` zakresu.|
|[pos_type](#pos_type)|Sprawia, że tego typu w ramach `basic_filebuf`firmy odpowiednikiem typu o takiej samej nazwie w zakresie `Tr` zakresu.|
|[traits_type](#traits_type)|Kojarzy nazwę typu z `Tr` parametru szablonu.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[close](#close)|Zamyka plik.|
|[is_open](#is_open)|Wskazuje, czy plik jest otwarty.|
|[open](#open)|Otwiera plik.|
|[overflow](#overflow)|Chronione funkcja wirtualna, która może być wywoływana po wstawieniu do buforu pełnej nowego znaku.|
|[pbackfail](#pbackfail)|Funkcja chroniony element członkowski wirtualnego próbuje odłożyć element do strumienia wejściowego, a następnie wprowadź go bieżącego elementu (wskazywany przez wskaźnik następnej).|
|[seekoff](#seekoff)|Chronione wirtualna funkcja składowa próbuje alter dla strumieni kontrolowanego bieżącej pozycji.|
|[seekpos —](#seekpos)|Chronione wirtualna funkcja składowa próbuje alter dla strumieni kontrolowanego bieżącej pozycji.|
|[setbuf](#setbuf)|Funkcja chroniony element członkowski wirtualnego wykonuje określonego operacji, aby każdy bufor strumienia pochodnej.|
|[swap](#swap)|Wymienia zawartość tego `basic_filebuf` zawartości dotyczącej dostępnego `basic_filebuf` parametru.|
|[sync](#sync)|Funkcja chroniony, wirtualny próbuje synchronizował kontrolowanego strumienie skojarzone strumieni zewnętrznych.|
|[uflow](../standard-library/basic-streambuf-class.md#uflow)|Chroniona funkcja wirtualna, aby wyodrębnić bieżącego elementu ze strumienia wejściowego.|
|[underflow](#underflow)|Chroniona funkcja wirtualna, aby wyodrębnić bieżącego elementu ze strumienia wejściowego.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<fstream — >

**Namespace:** standardowe

## <a name="basic_filebuf"></a>  basic_filebuf::basic_filebuf

Tworzy obiekt typu `basic_filebuf`.

```cpp
basic_filebuf();

basic_filebuf(basic_filebuf&& right);
```

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor przechowuje wskaźnik zerowy wszystkie wskaźniki kontrolowanie buforu wejściowego i bufor wyjściowy. Przechowuje także wskaźnik zerowy we wskaźniku pliku.

Drugi Konstruktor inicjuje obiekt z zawartością `right`, traktowane jako odwołanie rvalue.

## <a name="char_type"></a>  basic_filebuf::char_type

Kojarzy nazwę typu z `Elem` parametru szablonu.

```cpp
typedef Elem char_type;
```

## <a name="close"></a>  basic_filebuf::Close

Zamyka plik.

```cpp
basic_filebuf<Elem, Tr> *close();
```

### <a name="return-value"></a>Wartość zwracana

Funkcja elementu członkowskiego zwraca wskaźnikiem typu null, jeśli wskaźnik pliku jest wskaźnikiem typu null.

### <a name="remarks"></a>Uwagi

`close` wywołania `fclose`( **fp**). Jeśli ta funkcja zwraca wartość różną od zera, funkcja zwraca pusty wskaźnik. W przeciwnym razie zwraca **to** do wskazania, że plik został pomyślnie zamknięty.

Dla szerokiego strumienia, jeśli wszystkie wstawienia miały miejsce od czasu otwarcia strumienia lub od momentu ostatniego wywołania do `streampos`, wywołania funkcji [przepełnienie](#overflow). Wstawia dowolnej sekwencji niezbędne do przywrócenia stanu początkowego konwersji przy użyciu pliku reguł konwersji `fac` do wywołania `fac.unshift` zgodnie z potrzebami. Każdy element `byte` typu **char** generowany w związku z tym są zapisywane do skojarzonego strumienia wyznaczony przez wskaźnik pliku `fp` tak jak za kolejnych wywołań formularza `fputc`( **bajtów**, **fp**). Jeśli wywołanie `fac.unshift` lub wszelkie zapisu kończy się niepowodzeniem, funkcja kończy się niepowodzeniem.

### <a name="example"></a>Przykład

Poniższy przykład przyjmuje dwa pliki w bieżącym katalogu: basic_filebuf_close.txt (zawartość jest "Testowanie") i iotest.txt (zawartość jest "SSS").

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

## <a name="int_type"></a>  basic_filebuf::int_type

Sprawia, że tego typu w zakresie firmy basic_filebuf — odpowiednikiem typu o takiej samej nazwie w `Tr` zakresu.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="is_open"></a>  basic_filebuf::is_open

Wskazuje, czy plik jest otwarty.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli wskaźnik pliku nie jest wskaźnikiem typu null.

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

## <a name="off_type"></a>  basic_filebuf::off_type

Sprawia, że tego typu w zakresie firmy basic_filebuf — odpowiednikiem typu o takiej samej nazwie w `Tr` zakresu.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="open"></a>  basic_filebuf::Open

Otwiera plik.

```cpp
basic_filebuf<Elem, Tr> *open(
    const char* _Filename,
    ios_base::openmode _Mode,
    int _Prot = (int)ios_base::_Openprot);

basic_filebuf<Elem, Tr> *open(
    const char* _Filename,
    ios_base::openmode _Mode);

basic_filebuf<Elem, Tr> *open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode,
    int _Prot = (int)ios_base::_Openprot);

basic_filebuf<Elem, Tr> *open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode);
```

### <a name="parameters"></a>Parametry

*Nazwa p_liku*<br/>
Nazwa pliku, aby otworzyć.

*_Tryb*<br/>
Jedno z wyliczeń w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*<br/>
Domyślny plik otwarcie ochrony odpowiednikiem *shflag* parametru w [_fsopen —, _wfsopen —](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="return-value"></a>Wartość zwracana

Jeśli wskaźnik pliku jest wskaźnikiem typu null, funkcja zwraca pusty wskaźnik. W przeciwnym razie zwraca **to**.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego otwiera plik o nazwie pliku *filename*, wywołując [fopen —](../c-runtime-library/reference/fopen-wfopen.md)( *filename*, **strmode**). `strmode` jest określana na podstawie **trybu &**~ ( [zjadło](../standard-library/ios-base-class.md#openmode) & &#124; [binarne](../standard-library/ios-base-class.md#openmode)):

- `ios_base::in` staje się **"r"** (Otwórz istniejący plik do odczytu).

- [ios_base::Out](../standard-library/ios-base-class.md#fmtflags) lub **ios_base::out &#124; ios_base::trunc** staje się **"w"** (obciąć istniejący plik lub utwórz do zapisu).

- **ios_base::Out &#124; aplikacji** staje się **""** (Otwórz istniejący plik do wykonania operacji dołączania wszystkie operacje zapisu).

- **ios_base::in &#124; ios_base::out** staje się **"r +"** (Otwórz istniejący plik do odczytu i zapisu).

- **ios_base::in &#124; ios_base::out &#124; ios_base::trunc** staje się **"w +"** (obciąć istniejący plik lub utwórz do odczytu i zapisu).

- **ios_base::in &#124; ios_base::out &#124; ios_base::app** staje się **"+"** (Otwórz istniejący plik do odczytu i dołączania wszystkie operacje zapisu).

Jeśli **trybu & ios_base::binary** jest różna od zera, dołącza funkcję `b` do `strmode` można otworzyć strumienia binarnego zamiast strumieniu tekstu. Następnie przechowuje wartość zwrócona przez obiekt `fopen` we wskaźniku pliku `fp`. Jeśli **trybu & ios_base::ate** jest różna od zera, a wskaźnikiem pliku nie jest wskaźnikiem typu null, wywołania funkcji `fseek`( **fp**, 0, `SEEK_END`) do pozycji w strumieniu na końcu pliku. Jeśli ten pozycjonowania operacja zakończy się niepowodzeniem, wywołania funkcji [Zamknij](#close)( `fp`) i przechowuje wskaźnik zerowy we wskaźniku pliku.

Jeśli wskaźnik pliku nie jest wskaźnikiem typu null, funkcja określa zestaw reguł konwersji plików: `use_facet` <  `codecvt` <  **Elem**, `char`, **traits_type::** [ state_type](../standard-library/char-traits-struct.md#state_type)>> ( [getloc —](../standard-library/basic-streambuf-class.md#getloc)), do użytku przez [niedopełnienie](#underflow) i [przepełnienie](#overflow).

Jeśli wskaźnik pliku jest wskaźnikiem typu null, funkcja zwraca pusty wskaźnik. W przeciwnym razie zwraca **to**.

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::close](#close) przykład, który używa `open`.

## <a name="op_eq"></a>  basic_filebuf::operator =

Przypisz zawartość tego obiektu buforu strumienia. Jest to przeniesienia przypisania obejmujące rvalue, który nie pozostawione kopię.

```cpp
basic_filebuf& operator=(basic_filebuf&& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Odwołania rvalue do [basic_filebuf —](../standard-library/basic-filebuf-class.md) obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca * to.

### <a name="remarks"></a>Uwagi

Operator składowy zastępuje zawartość obiektu przy użyciu zawartości *prawo*, traktowane jako odwołanie rvalue. Aby uzyskać więcej informacji, zobacz [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="overflow"></a>  basic_filebuf::Overflow

Wywołuje się, gdy znak nowego są wstawiane do pełnego buforu.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>Parametry

*_Meta*<br/>
Znak do wstawienia w buforze lub `traits_type::eof`.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie powiedzie się, zwraca `traits_type::eof`. W przeciwnym razie zwraca **traits_type::**[not_eof —](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).

### <a name="remarks"></a>Uwagi

Jeśli *_Meta* **! = traits_type::**[eof](../standard-library/char-traits-struct.md#eof), chronionych wirtualna funkcja składowa usiłują Wstaw element **ch = traits_type::** [ to_char_type —](../standard-library/char-traits-struct.md#to_char_type)(*_Meta*) do buforu danych wyjściowych. Jego można to zrobić na różne sposoby:

- W przypadku pozycji zapisu jest dostępny, można przechowywać element w określonej pozycji zapisu i zwiększyć wskaźnik następnej dla buforu danych wyjściowych.

- Go można udostępnić pozycji zapisu, przydzielając nowej lub dodatkowej pamięci masowej dla buforu danych wyjściowych.

- Umożliwia on konwertowanie żadnych oczekujących danych wyjściowych w buforze danych wyjściowych, a następnie `ch`, przy użyciu pliku reguł konwersji `fac` do wywołania `fac.out` zgodnie z potrzebami. Każdy element `ch` typu *char* generowany w związku z tym są zapisywane do skojarzonego strumienia wyznaczony przez wskaźnik pliku `fp` tak jak za kolejnych wywołań formularza `fputc`( **ch**, **fp**). W przypadku niepowodzenia konwersji ani zapisu funkcja kończy się niepowodzeniem.

## <a name="pbackfail"></a>  basic_filebuf::pbackfail

Próbuje odłożyć element do strumienia wejściowego, a następnie wprowadź go bieżącego elementu (wskazywany przez wskaźnik następnej).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>Parametry

*_Meta*<br/>
Znak do wstawienia do określonego bufora lub `traits_type::eof`.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie powiedzie się, zwraca `traits_type::eof`. W przeciwnym razie zwraca **traits_type::**[not_eof —](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).

### <a name="remarks"></a>Uwagi

Funkcja chroniony element członkowski wirtualnego przywraca element do buforu wejściowego i udostępnia je po bieżącego elementu (wskazywany przez wskaźnik następnej). Jeśli _ *Meta* **== traits_type::**[eof](../standard-library/char-traits-struct.md#eof), element do usunięcia jest skutecznie już w strumieniu przed bieżącego elementu. W przeciwnym razie ten element został zastąpiony **ch = traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(\_ *Meta*). Funkcję można odłożyć element na różne sposoby:

- Jeśli pozycja putback — i element tam przechowywane w porównaniu równa `ch`, jego dekrementacja wskaźnik następnej dla buforu danych wejściowych.

- Jeśli funkcja mogą wysyłać `putback` pozycji dostępny, można to zrobić, ustaw wskaźnik dalej, aby wskazywała na położenie i przechowywać `ch` w tym miejscu.

- Jeśli funkcja wypchnąć ponownie element na strumień wejściowy, go to zrobić, takie jak przez wywołanie metody `ungetc` dla elementu typu **char**.

## <a name="pos_type"></a>  basic_filebuf::pos_type

Sprawia, że tego typu w zakresie firmy basic_filebuf — odpowiednikiem typu o takiej samej nazwie w `Tr` zakresu.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="seekoff"></a>  basic_filebuf::seekoff

Próbuje zmienić dla strumieni kontrolowanego bieżącej pozycji.

```cpp
virtual pos_type seekoff(off_type _Off,
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

Zwraca nową pozycję lub nieprawidłowy strumień pozycji.

### <a name="remarks"></a>Uwagi

Funkcja chroniony element członkowski wirtualnego usiłują alter dla strumieni kontrolowanego bieżącej pozycji. Dla obiektu klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>, pozycja strumień może być reprezentowany przez obiekt typu `fpos_t`, która przechowuje przesunięcie i wszelkich informacji o stanie potrzebne do Przeanalizuj szerokiego strumień. Przesunięcia zero Określa pierwszy element strumienia. (Obiekt typu [pos_type](../standard-library/basic-streambuf-class.md#pos_type) są przechowywane co najmniej `fpos_t` obiektu.)

Strumienie wejściowe i wyjściowe dla pliku, otworzyć do odczytu i zapisu, są umieszczone tandem. Aby przełączać się między wstawiania i wyodrębniania, należy wywołać, albo [pubseekoff —](../standard-library/basic-streambuf-class.md#pubseekoff) lub [pubseekpos —](../standard-library/basic-streambuf-class.md#pubseekpos). Wywołania `pubseekoff` (a tym samym do `seekoff`) mają różne ograniczenia dotyczące [strumienie tekstu](../c-runtime-library/text-and-binary-streams.md), [strumieni binarnych](../c-runtime-library/text-and-binary-streams.md), i [szerokie strumienie](../c-runtime-library/byte-and-wide-streams.md).

Jeśli wskaźnik pliku `fp` jest pustym wskaźnikiem, funkcja kończy się niepowodzeniem. W przeciwnym razie usiłują zmiany pozycji strumienia, wywołując `fseek`( **fp**, `_Off`, `_Way`). Jeśli ta funkcja zakończy się powodzeniem i wynikowy pozycji `fposn` można ustalić, wywołując `fgetpos`( **fp**, **& fposn**), funkcja się powiedzie. Jeśli funkcja się powiedzie, funkcja zwraca wartość typu `pos_type` zawierający `fposn`. W przeciwnym razie zwraca położenie nieprawidłowy strumień.

## <a name="seekpos"></a>  basic_filebuf::seekpos

Próbuje zmienić dla strumieni kontrolowanego bieżącej pozycji.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*<br/>
Położenie do wyszukania dla.

*_Which*<br/>
Określa tryb pozycję wskaźnika. Wartość domyślna to umożliwia modyfikowanie, Odczyt i zapis pozycji.

### <a name="return-value"></a>Wartość zwracana

Jeśli wskaźnik pliku `fp` jest pustym wskaźnikiem, funkcja kończy się niepowodzeniem. W przeciwnym razie usiłują zmiany pozycji strumienia, wywołując `fsetpos`( **fp**, **& fposn**), gdzie `fposn` jest `fpos_t` obiektu przechowywanego w `pos`. Jeśli ta funkcja zakończy się powodzeniem, funkcja zwraca `pos`. W przeciwnym razie zwraca położenie nieprawidłowy strumień. Aby określić, jeśli pozycja strumienia jest nieprawidłowa, porównaj wartość zwracaną z `pos_type(off_type(-1))`.

### <a name="remarks"></a>Uwagi

Funkcja chroniony element członkowski wirtualnego usiłują alter dla strumieni kontrolowanego bieżącej pozycji. Dla obiektu klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md) \< **Elem**, **Tr**>, pozycja strumień może być reprezentowany przez obiekt typu `fpos_t`, które sklepy Przesunięcie i wszelkich informacji o stanie potrzebnych do analizy strumienia szeroki. Przesunięcia zero Określa pierwszy element strumienia. (Obiekt typu `pos_type` są przechowywane co najmniej `fpos_t` obiektu.)

Strumienie wejściowe i wyjściowe dla pliku, otworzyć do odczytu i zapisu, są umieszczone tandem. Aby przełączać się między wstawiania i wyodrębniania, należy wywołać, albo [pubseekoff —](../standard-library/basic-streambuf-class.md#pubseekoff) lub [pubseekpos —](../standard-library/basic-streambuf-class.md#pubseekpos). Wywołania `pubseekoff` (a tym samym do `seekoff`) mają różne ograniczenia strumienie tekstu, strumienie binarne i szerokie strumienie.

Dla szerokiego strumienia, jeśli wszystkie wstawienia miały miejsce od czasu otwarcia strumienia lub od momentu ostatniego wywołania do `streampos`, wywołania funkcji [przepełnienie](#overflow). Wstawia dowolnej sekwencji niezbędne do przywrócenia stanu początkowego konwersji przy użyciu pliku reguł konwersji `fac` do wywołania **fac** `.unshift` zgodnie z potrzebami. Każdy element `byte` typu **char** generowany w związku z tym są zapisywane do skojarzonego strumienia wyznaczony przez wskaźnik pliku `fp` tak jak za kolejnych wywołań formularza `fputc`( **bajtów**, **fp**). Jeśli wywołanie `fac.unshift` lub wszelkie zapisu kończy się niepowodzeniem, funkcja kończy się niepowodzeniem.

## <a name="setbuf"></a>  basic_filebuf::setbuf

Wykonuje określonego operacji, aby każdy bufor strumienia pochodnej.

```cpp
virtual basic_streambuf<Elem, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*Właściwość _Buffer*<br/>
Wskaźnik do buforu.

*Liczba*<br/>
Rozmiar buforu.

### <a name="return-value"></a>Wartość zwracana

Chroniona funkcja elementu członkowskiego zwraca zero, jeśli wskaźnik pliku `fp` jest wskaźnikiem wartości null.

### <a name="remarks"></a>Uwagi

`setbuf` wywołania `setvbuf`( **fp**, ( `char` \*) `_Buffer`, `_IOFBF`, `count` \* `sizeof` ( **Elem**)) do zaoferowania tablicy z `count` elementów, poczynając od _ *buforu* jako bufor dla strumienia. Jeśli ta funkcja zwraca wartość różną od zera, funkcja zwraca pusty wskaźnik. W przeciwnym razie zwraca **to** Powodzenie sygnału.

## <a name="swap"></a>  basic_filebuf::swap

Wymienia zawartość tych `basic_filebuf` dla zawartości dotyczącej dostępnego `basic_filebuf`.

```cpp
void swap(basic_filebuf& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
`lvalue` Odwołanie do innego `basic_filebuf`.

## <a name="sync"></a>  basic_filebuf::Sync

Próbuje synchronizował kontrolowanego strumienie skojarzone strumieni zewnętrznych.

```cpp
virtual int sync();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca zero, jeśli wskaźnik pliku `fp` jest wskaźnikiem wartości null. W przeciwnym razie zwraca zero tylko wtedy, gdy wywołuje zarówno [przepełnienie](#overflow) i `fflush`( **fp**) odnieść sukces w opróżnianie wszelkie oczekujące dane wyjściowe do strumienia.

## <a name="traits_type"></a>  basic_filebuf::traits_type

Kojarzy nazwę typu z `Tr` parametru szablonu.

```cpp
typedef Tr traits_type;
```

## <a name="underflow"></a>  basic_filebuf::underflow

Wyodrębnia bieżącego elementu ze strumienia wejściowego.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie powiedzie się, zwraca **traits_type::**[eof](../standard-library/char-traits-struct.md#eof). W przeciwnym razie zwraca `ch`konwersji, zgodnie z opisem w sekcji uwag.

### <a name="remarks"></a>Uwagi

Chronione wirtualna funkcja składowa usiłują wyodrębnić bieżącego elementu `ch` wejściowego strumienia i zwracać element jako **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)(`ch`). Jego można to zrobić na różne sposoby:

- Jeśli pozycji odczytu jest dostępny, zajmuje `ch` elementu przechowywanego w pozycji odczytu i przesuwa wskaźnik następnej dla buforu danych wejściowych.

- Może odczytywać, jeden lub więcej elementów typu **char**, tak, jakby przez kolejnych wywołań formularza `fgetc`(**fp**) i konwertować je na element **ch** typu `Elem`przy użyciu fac reguł konwersji plików do wywoływania `fac.in` zgodnie z potrzebami. Jeśli odczyt ani konwersji nie powiedzie się, funkcja kończy się niepowodzeniem.

## <a name="see-also"></a>Zobacz także

[\<fstream>](../standard-library/fstream.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
