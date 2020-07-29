---
title: Klasa CMemFile
description: Zawiera opis funkcji dostępnych w klasie CMemFile, które umożliwiają współdziałanie z plikami pamięci.
ms.date: 07/23/2020
f1_keywords:
- CMemFile
- AFX/CMemFile
- AFX/CMemFile::CMemFile
- AFX/CMemFile::Attach
- AFX/CMemFile::Detach
- AFX/CMemFile::Alloc
- AFX/CMemFile::Free
- AFX/CmemFile::GetBufferPtr
- AFX/CMemFile::GrowFile"
- AFX/CMemFile::Memcpy
- AFX/CMemFile::Realloc
helpviewer_keywords:
- CMemFile [MFC], CMemFile
- CMemFile [MFC], Attach
- CMemFile [MFC], Detach
- CMemFile [MFC], Alloc
- CMemFile [MFC], Free
- CMemFile [MFC], GetBufferPtr
- CMemFile [MFC], GrowFile
- CMemFile [MFC], Memcpy
- CMemFile [MFC], Realloc
ms.assetid: 20e86515-e465-4f73-b2ea-e49789d63165
ms.openlocfilehash: edd1d8b8d3979427602bdb61fc7647aec15d58b5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222943"
---
# <a name="cmemfile-class"></a>Klasa CMemFile

Klasa pochodna [CFile](../../mfc/reference/cfile-class.md), która obsługuje pliki pamięci.

## <a name="syntax"></a>Składnia

```
class CMemFile : public CFile
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMemFile::CMemFile](#cmemfile)|Tworzy obiekt pliku pamięci.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMemFile:: Attach](#attach)|Dołącza blok pamięci do `CMemFile` .|
|[CMemFile::D etach](#detach)|Odłącza blok pamięci z `CMemFile` i zwraca wskaźnik do bloku pamięci odłączonej.|
|[CMemFile::GetBufferPtr](#getbufferptr)|Pobierz lub Zapisz bufor pamięci, który wykonuje kopię zapasową pliku pamięci.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMemFile:: Alloc](#alloc)|Zastąpienie w celu zmodyfikowania zachowania alokacji pamięci.|
|[CMemFile:: Free](#free)|Zastąpienie w celu zmodyfikowania zachowania dealokacji pamięci.|
|[CMemFile::GrowFile](#growfile)|Przesłoń, aby zmodyfikować zachowanie podczas zwiększania pliku.|
|[CMemFile:: memcpy](#memcpy)|Przesłoń, aby zmodyfikować zachowanie kopiowania pamięci podczas odczytywania i zapisywania plików.|
|[CMemFile:: realloc](#realloc)|Zastąpienie w celu zmodyfikowania zachowania ponownej alokacji pamięci.|

## <a name="remarks"></a>Uwagi

Te pliki pamięci zachowują się jak pliki dysków, z wyjątkiem tego, że plik jest przechowywany w pamięci RAM, a nie na dysku. Plik pamięci jest przydatny dla:

- szybki magazyn tymczasowy
- Transferowanie nieprzetworzonych bajtów między procesami niezależnymi
- Transferowanie obiektów serializowanych między procesami niezależnymi

`CMemFile`obiekty mogą automatycznie przydzielać własne pamięci. Lub można dołączyć własny blok pamięci do `CMemFile` obiektu przez wywołanie metody [Attach](#attach). W obu przypadkach pamięć służąca do zwiększania rozmiaru pliku pamięci jest automatycznie alokowana, `nGrowBytes` Jeśli `nGrowBytes` nie jest równa zero.

Blok pamięci zostanie automatycznie usunięty po zniszczeniu `CMemFile` obiektu, jeśli pamięć została pierwotnie przyznana przez `CMemFile` obiekt; w przeciwnym razie użytkownik jest odpowiedzialny za cofnięcie przydziału pamięci dołączonej do obiektu.

Można uzyskać dostęp do bloku pamięci za pośrednictwem wskaźnika dostarczonego po odłączeniu go od `CMemFile` obiektu przez wywołanie [odłączenia](#detach).

Najbardziej typowym zastosowaniem `CMemFile` jest utworzenie `CMemFile` obiektu i użycie go przez wywołanie funkcji składowych [CFile](../../mfc/reference/cfile-class.md) . Tworzenie zostanie `CMemFile` automatycznie otwarte: nie jest wywoływana [CFile:: Open](../../mfc/reference/cfile-class.md#open), która jest używana tylko w przypadku plików dyskowych. Ponieważ `CMemFile` nie używa pliku dyskowego, element członkowski danych `CFile::m_hFile` nie jest używany.

`CFile`Funkcje składowe [duplikują](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange)i [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) nie są zaimplementowane dla programu `CMemFile` . Jeśli wywołasz te funkcje w `CMemFile` obiekcie, uzyskasz [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

`CMemFile`korzysta z biblioteki wykonawczej funkcje [malloc](../../c-runtime-library/reference/malloc.md), [realloc](../../c-runtime-library/reference/realloc.md)i [Free](../../c-runtime-library/reference/free.md) , aby przydzielić, ponownie przydzielić i cofnąć alokację pamięci; i wewnętrzna [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md) do blokowania pamięci kopiowania podczas odczytu i zapisu. Jeśli chcesz zmienić to zachowanie lub zachowanie podczas `CMemFile` zwiększania pliku, Utwórz własną klasę z `CMemFile` i Zastąp odpowiednie funkcje.

Aby uzyskać więcej informacji na temat `CMemFile` , zapoznaj się z artykułami [pliki w temacie MFC](../../mfc/files-in-mfc.md) i [zarządzania pamięcią (MFC)](../../mfc/memory-management.md) i zapoznaj się z tematem [Obsługa plików](../../c-runtime-library/file-handling.md) w *dokumentacji dotyczącej biblioteki wykonawczej*.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CMemFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

## <a name="cmemfilealloc"></a><a name="alloc"></a>CMemFile:: Alloc

Ta funkcja jest wywoływana przez `CMemFile` funkcję członkowską.

```
virtual BYTE* Alloc(SIZE_T nBytes);
```

### <a name="parameters"></a>Parametry

*nBytes*<br/>
Liczba bajtów pamięci do przydzielenia.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do bloku pamięci, który został przydzielony, lub wartość NULL, jeśli alokacja nie powiodła się.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję, aby zaimplementować niestandardową alokację pamięci. Jeśli zastąpisz tę funkcję, prawdopodobnie zechcesz również przesłonić opcję [bezpłatna](#free) i ponowna [alokacja](#realloc) .

Implementacja domyślna korzysta z funkcji biblioteki wykonawczej [malloc](../../c-runtime-library/reference/malloc.md) do przydzielenia pamięci.

## <a name="cmemfileattach"></a><a name="attach"></a>CMemFile:: Attach

Wywołaj tę funkcję, aby dołączyć blok pamięci do `CMemFile` .

```cpp
void Attach(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>Parametry

*lpBuffer*<br/>
Wskaźnik do bufora, do którego ma zostać dołączony `CMemFile` .

*nBufferSize*<br/>
Liczba całkowita określająca rozmiar buforu w bajtach.

*nGrowBytes*<br/>
Przyrost alokacji pamięci w bajtach.

### <a name="remarks"></a>Uwagi

Powoduje to `CMemFile` użycie bloku pamięci jako pliku pamięci.

Jeśli *nGrowBytes* ma wartość 0, `CMemFile` ustawi długość pliku na *nBufferSize*. Oznacza to, że dane w bloku pamięci przed dołączeniem do niego `CMemFile` zostaną użyte jako plik. Nie można wzrosnąć plików pamięci utworzonych w ten sposób.

Ponieważ nie można wzrosnąć pliku, należy zachować ostrożność, aby nie powodowały `CMemFile` próby powiększania pliku. Na przykład nie wywołuj `CMemFile` zastąpień [CFile: Write](../../mfc/reference/cfile-class.md#write) do zapisu poza końcem lub nie Wywołaj [CFile: SetLength](../../mfc/reference/cfile-class.md#setlength) o długości większej niż *nBufferSize*.

Jeśli wartość *nGrowBytes* jest większa niż 0, `CMemFile` program zignoruje zawartość dołączonego bloku pamięci. Musisz zapisać zawartość pliku pamięci od początku, używając `CMemFile` przesłonięcia `CFile::Write` . Jeśli próbujesz napisać poza końcem pliku lub zwiększyć plik `CMemFile` , wywołując przesłonięcie, zwiększy `CFile::SetLength` `CMemFile` alokację pamięci w przyrostach *nGrowBytes*. Zwiększanie alokacji pamięci zakończy się niepowodzeniem, jeśli blok pamięci przekazany do `Attach` nie został przydzielony przy użyciu metody zgodnej z [alokacją](#alloc). Aby była zgodna z domyślną implementacją programu `Alloc` , należy przydzielić pamięć z funkcją biblioteki wykonawczej [malloc](../../c-runtime-library/reference/malloc.md) lub [calloc](../../c-runtime-library/reference/calloc.md).

## <a name="cmemfilecmemfile"></a><a name="cmemfile"></a>CMemFile::CMemFile

Pierwsze Przeciążenie spowoduje otwarcie pustego pliku pamięci.

```
CMemFile(UINT nGrowBytes = 1024);

CMemFile(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>Parametry

*nGrowBytes*<br/>
Przyrost alokacji pamięci w bajtach.

*lpBuffer* Wskaźnik do buforu, który odbiera informacje o rozmiarze *nBufferSize*.

*nBufferSize*<br/>
Liczba całkowita określająca rozmiar buforu pliku w bajtach.

### <a name="remarks"></a>Uwagi

Plik jest otwierany przez konstruktora. Nie wywołuj [CFile:: Open](../../mfc/reference/cfile-class.md#open).

Drugie Przeciążenie działa tak samo, jak w przypadku używania pierwszego konstruktora i natychmiastowego [dołączania](#attach) z tymi samymi parametrami. Aby uzyskać szczegółowe informacje, zobacz opis funkcji `Attach`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#36](../../atl-mfc-shared/reference/codesnippet/cpp/cmemfile-class_1.cpp)]

## <a name="cmemfiledetach"></a><a name="detach"></a>CMemFile::D etach

Wywołaj tę funkcję, aby uzyskać wskaźnik do bloku pamięci używanego przez program `CMemFile` .

```
BYTE* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do bloku pamięci, który zawiera zawartość pliku pamięci.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji powoduje także zamknięcie `CMemFile` . Możesz ponownie dołączyć blok pamięci do `CMemFile` przez wywołanie metody [Attach](#attach). Jeśli chcesz ponownie dołączyć plik i użyć w nim danych, należy wywołać [CFile:: GetLength](../../mfc/reference/cfile-class.md#getlength) , aby pobrać długość pliku przed wywołaniem `Detach` . W przypadku dołączenia bloku pamięci do programu, aby `CMemFile` można było użyć jego danych ( `nGrowBytes` = = 0), nie można zwiększyć pliku pamięci.

## <a name="cmemfilefree"></a><a name="free"></a>CMemFile:: Free

Ta funkcja jest wywoływana przez `CMemFile` funkcję członkowską.

```
virtual void Free(BYTE* lpMem);
```

### <a name="parameters"></a>Parametry

*lpMem*<br/>
Wskaźnik do pamięci, która ma zostać cofnięta alokacja.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję, aby zaimplementować niestandardową alokację pamięci. Jeśli zastąpisz tę funkcję, prawdopodobnie zajdzie potrzeba przesłonięcia [alokacji](#alloc) i [alokacji](#realloc) .

## <a name="cmemfilegetbufferptr"></a><a name="getbufferptr"></a>CMemFile::GetBufferPtr

Pobierz lub Zapisz bufor pamięci, który wykonuje kopię zapasową pliku pamięci.

```cpp
virtual UINT GetBufferPtr(
    UINT nCommand,
    UINT nCount = 0,
    void** ppBufStart = NULL,
    void** ppBufMax = NULL
);
```

### <a name="parameters"></a>Parametry

*Nwykonywane polecenie*<br/>
[BufferCommand](buffercommand-enumeration.md) do przeprowadzenia ( `bufferCheck` , `bufferCommit` , `bufferRead` lub `bufferWrite` ).

*nCount*<br/>
W zależności od *nwykonywane polecenie*liczba bajtów w buforze do odczytu, zapisu lub zatwierdzenia. Podczas odczytywania z buforu należy określić wartość-1, aby przywrócić bufor z bieżącego położenia do końca pliku.

*ppBufStart*<br/>
określoną Początek buforu. Musi być `NULL` *nwykonywane polecenie* `bufferCommit` .

*ppBufMax*<br/>
określoną Koniec buforu. Musi być `NULL` nwykonywane polecenie `bufferCommit` .

### <a name="return-value"></a>Wartość zwracana

| wartość *polecenia* | Wartość zwracana |
|--|--|
| `buffercheck` | Zwraca [bufferDirect](buffercommand-enumeration.md) , jeśli jest obsługiwane bezpośrednie buforowanie, w przeciwnym razie 0. |
| `bufferCommit` | Typu`0` |
| `bufferRead` lub `bufferWrite` | Zwraca liczbę bajtów w zwracanym obszarze buforu. *ppBufStart* i *ppBufMax* wskazują początek i koniec buforu odczytu/zapisu.  |

### <a name="remarks"></a>Uwagi

Bieżąca pozycja w buforze pamięci ( `m_nPosition` ) jest zaawansowana w następujący sposób, w zależności od *nwykonywane polecenie*:

| *Nwykonywane polecenie* | położenie buforu |
|-|-|
| `bufferCommit` | Bieżąca pozycja postępuje zgodnie z rozmiarem zatwierdzonego buforu. |
| `bufferRead` | Bieżąca pozycja jest zwiększana o rozmiar buforu odczytu. |

## <a name="cmemfilegrowfile"></a><a name="growfile"></a>CMemFile::GrowFile

Ta funkcja jest wywoływana przez kilka `CMemFile` funkcji Członkowskich.

```
virtual void GrowFile(SIZE_T dwNewLen);
```

### <a name="parameters"></a>Parametry

*dwNewLen*<br/>
Nowy rozmiar pliku pamięci.

### <a name="remarks"></a>Uwagi

Można zastąpić go, jeśli chcesz zmienić sposób `CMemFile` zwiększania jego pliku. Domyślna [alokacja](#realloc) wywołań implementacji pozwala rozwijać istniejący blok (lub [Alloc](#alloc) w celu utworzenia bloku pamięci), przydzielanie pamięci w wielokrotnościach `nGrowBytes` wartości określonej w konstruktorze lub [dołączanie](#attach) wywołania.

## <a name="cmemfilememcpy"></a><a name="memcpy"></a>CMemFile:: memcpy

Ta funkcja jest wywoływana przez `CMemFile` zastąpienia elementu [CFile:: Read](../../mfc/reference/cfile-class.md#read) i [CFile:: Write](../../mfc/reference/cfile-class.md#write) w celu przeniesienia danych do i z pliku pamięci.

```
virtual BYTE* Memcpy(
    BYTE* lpMemTarget,
    const BYTE* lpMemSource,
    SIZE_T nBytes);
```

### <a name="parameters"></a>Parametry

*lpMemTarget*<br/>
Wskaźnik do bloku pamięci, do którego zostanie skopiowana pamięć źródłowa.

*lpMemSource*<br/>
Wskaźnik do bloku pamięci źródłowej.

*nBytes*<br/>
Liczba bajtów do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Kopia *lpMemTarget*.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję, jeśli chcesz zmienić sposób, w jaki `CMemFile` te kopie pamięci są używane.

## <a name="cmemfilerealloc"></a><a name="realloc"></a>CMemFile:: realloc

Ta funkcja jest wywoływana przez `CMemFile` funkcję członkowską.

```
virtual BYTE* Realloc(
    BYTE* lpMem,
    SIZE_T nBytes);
```

### <a name="parameters"></a>Parametry

*lpMem*<br/>
Wskaźnik do bloku pamięci do przydzielenia.

*nBytes*<br/>
Nowy rozmiar bloku pamięci.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do bloku pamięci, który został ponownie przydzielony (i prawdopodobnie przeniesiony), lub wartość NULL, jeśli ponowne przypisanie nie powiodło się.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję, aby zaimplementować niestandardową ponowną alokację pamięci. Jeśli zastąpisz tę funkcję, prawdopodobnie zajdzie potrzeba przesłonięcia [alokacji](#alloc) i [zwolnienia](#free) .

## <a name="see-also"></a>Zobacz także

[Klasa CFile](../../mfc/reference/cfile-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
