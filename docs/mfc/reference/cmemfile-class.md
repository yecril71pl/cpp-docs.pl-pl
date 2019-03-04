---
title: CMemFile Class
ms.date: 11/04/2016
f1_keywords:
- CMemFile
- AFX/CMemFile
- AFX/CMemFile::CMemFile
- AFX/CMemFile::Attach
- AFX/CMemFile::Detach
- AFX/CMemFile::Alloc
- AFX/CMemFile::Free
- AFX/CMemFile::GrowFile
- AFX/CMemFile::Memcpy
- AFX/CMemFile::Realloc
helpviewer_keywords:
- CMemFile [MFC], CMemFile
- CMemFile [MFC], Attach
- CMemFile [MFC], Detach
- CMemFile [MFC], Alloc
- CMemFile [MFC], Free
- CMemFile [MFC], GrowFile
- CMemFile [MFC], Memcpy
- CMemFile [MFC], Realloc
ms.assetid: 20e86515-e465-4f73-b2ea-e49789d63165
ms.openlocfilehash: a57f4e245ca1e93ec0edd454a7f407aeda5beca4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304949"
---
# <a name="cmemfile-class"></a>CMemFile Class

[CFile](../../mfc/reference/cfile-class.md)-pochodne klasy, która obsługuje pliki w pamięci.

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
|[CMemFile::Attach](#attach)|Dołącza bloku pamięci, aby `CMemFile`.|
|[CMemFile::Detach](#detach)|Odłącza blok pamięci z `CMemFile` i zwraca wskaźnik do bloku pamięci odłączone.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMemFile::Alloc](#alloc)|Należy przesłonić, aby zmodyfikować zachowanie alokacji pamięci.|
|[CMemFile::Free](#free)|Należy przesłonić, aby zmodyfikować zachowanie dezalokacji pamięci.|
|[CMemFile::GrowFile](#growfile)|Należy przesłonić, aby zmodyfikować zachowanie podczas powiększania pliku.|
|[CMemFile::Memcpy](#memcpy)|Należy przesłonić ten element, aby zmodyfikować zachowanie kopiowania pamięci podczas odczytywania i zapisywania plików.|
|[CMemFile::Realloc](#realloc)|Należy przesłonić, aby zmodyfikować zachowanie ponownej alokacji pamięci.|

## <a name="remarks"></a>Uwagi

Te pliki pamięci zachowują się jak plików na dysku, z tą różnicą, że plik jest przechowywany w pamięci RAM, a nie na dysku. Plik pamięci jest przydatna, błyskawicznie obsługiwany magazyn tymczasowy lub transferu bajtów raw lub serializacji obiektów między procesami niezależne.

`CMemFile` obiekty może automatycznie przydzielać własne pamięci lub możesz dołączyć własnego bloku pamięci `CMemFile` obiektu przez wywołanie metody [Dołącz](#attach). W obu przypadkach pamięci dla automatycznego powiększania pliku pamięci są przydzielane w `nGrowBytes`-o rozmiarze co, jeśli `nGrowBytes` nie jest równa zero.

Blok pamięci zostanie automatycznie usunięte podczas niszczenia `CMemFile` obiektu, jeśli pamięć została pierwotnie przydzielonej przez `CMemFile` obiektu; w przeciwnym razie są odpowiedzialne za dealokowanie pamięci dołączony do obiektu.

Dostęp do bloku pamięci za pomocą wskaźnika dostarczony po odłączeniu od `CMemFile` obiektu przez wywołanie metody [Odłącz](#detach).

Najbardziej powszechnym zastosowaniem programu `CMemFile` polega na utworzeniu `CMemFile` obiektu i korzystać z niego, wywołując [CFile](../../mfc/reference/cfile-class.md) funkcji elementów członkowskich. Należy pamiętać, że tworzenie `CMemFile` automatycznie zostanie otwarty: Nie wywołuj [CFile::Open](../../mfc/reference/cfile-class.md#open), która służy tylko do plików na dysku. Ponieważ `CMemFile` nie korzysta z plikiem dyskowym element członkowski danych `CFile::m_hFile` nie jest używany.

`CFile` Elementów członkowskich [zduplikowane](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange), i [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) nie są zaimplementowane dla `CMemFile`. Jeśli chcesz wywołać te funkcje w `CMemFile` obiektów, zostanie wyświetlony [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

`CMemFile` używa funkcji biblioteki wykonawczej [— funkcja malloc](../../c-runtime-library/reference/malloc.md), [realloc](../../c-runtime-library/reference/realloc.md), i [bezpłatne](../../c-runtime-library/reference/free.md) do przydzielania, ponownego przydzielenia i cofnięcie przydziału pamięci; i wewnętrznych [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md) bloku kopiowania pamięci podczas odczytywania i zapisywania. Jeśli chcesz zmienić to zachowanie lub zachowanie podczas `CMemFile` rozwoju pliku pochodną klasy z `CMemFile` i zastąpić odpowiednie funkcje.

Aby uzyskać więcej informacji na temat `CMemFile`, zobacz artykuły [pliki w MFC](../../mfc/files-in-mfc.md) i [zarządzania pamięci (MFC)](../../mfc/memory-management.md) zobaczyć [Obsługa plików](../../c-runtime-library/file-handling.md) w *Run-Time Odwołanie do biblioteki*.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CMemFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="alloc"></a>  CMemFile::Alloc

Ta funkcja jest wywoływana `CMemFile` funkcji elementów członkowskich.

```
virtual BYTE* Alloc(SIZE_T nBytes);
```

### <a name="parameters"></a>Parametry

*nBytes*<br/>
Liczba bajtów pamięci do przydzielenia.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do bloku pamięci, która została przydzielona, lub wartość NULL, jeśli alokacja nie powiodła się.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę funkcję, aby zaimplementować alokacji pamięci niestandardowych. Jeśli zastąpisz tę funkcję, prawdopodobnie należy zastąpić [bezpłatna](#free) i [Realloc](#realloc) także.

Domyślna implementacja używa funkcji biblioteki wykonawczej [— funkcja malloc](../../c-runtime-library/reference/malloc.md) można przydzielić pamięci.

##  <a name="attach"></a>  CMemFile::Attach

Wywołaj tę funkcję, aby dołączyć blok pamięci, aby `CMemFile`.

```
void Attach(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>Parametry

*lpBuffer*<br/>
Wskaźnik do buforu do podłączenia do `CMemFile`.

*nBufferSize*<br/>
Liczba całkowita określająca rozmiar buforu w bajtach.

*nGrowBytes*<br/>
Zwiększenie przydziału pamięci w bajtach.

### <a name="remarks"></a>Uwagi

Powoduje to, że `CMemFile` używany blok pamięci jako pliku pamięci.

Jeśli *nGrowBytes* ma wartość 0, `CMemFile` ustawi długość pliku *nBufferSize*. Oznacza to, że dane w bloku pamięci zanim został dołączony do `CMemFile` będzie służyć jako plik. Pliki w pamięci utworzone w ten sposób nie można zwiększyć.

Ponieważ plik nie może być organicznie, należy uważać, aby nie spowodować `CMemFile` próbę rozwijać pliku. Na przykład nie wywołuj `CMemFile` przesłonięć o [CFile:Write](../../mfc/reference/cfile-class.md#write) do zapisu poza końcem lub Nie wywołuj [CFile:SetLength](../../mfc/reference/cfile-class.md#setlength) o długości maksymalnie *nBufferSize*.

Jeśli *nGrowBytes* jest większa niż 0, `CMemFile` zignoruje zawartość bloku pamięci jest podłączona. Musisz zapisać zawartość pliku pamięci od podstaw przy użyciu `CMemFile` zastępowania `CFile::Write`. Jeśli próba zapisu poza końcem pliku lub Rozwijaj go przez wywołanie metody `CMemFile` zastępowania `CFile::SetLength`, `CMemFile` będzie się zwiększać alokacji pamięci, z przyrostem równym *nGrowBytes*. Rośnie alokacji pamięci zakończy się niepowodzeniem, jeśli blok pamięci, możesz przekazać do `Attach` nie można przydzielić przy użyciu metody, które są zgodne z [alokacji](#alloc). Aby był zgodny z domyślną implementację elementu `Alloc`, należy przydzielić pamięci za pomocą funkcji biblioteki wykonawczej [— funkcja malloc](../../c-runtime-library/reference/malloc.md) lub [calloc](../../c-runtime-library/reference/calloc.md).

##  <a name="cmemfile"></a>  CMemFile::CMemFile

Pierwsze przeciążenie otwiera plik pusty pamięci.

```
CMemFile(UINT nGrowBytes = 1024);

CMemFile(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>Parametry

*nGrowBytes*<br/>
Zwiększenie przydziału pamięci w bajtach.

*lpBuffe*r wskaźnik do buforu, który otrzymuje informacje o rozmiarze *nBufferSize*.

*nBufferSize*<br/>
Liczba całkowita określająca rozmiar buforu pliku w bajtach.

### <a name="remarks"></a>Uwagi

Zwróć uwagę, że plik jest otwarty przez Konstruktor i że nie należy wywołać [CFile::Open](../../mfc/reference/cfile-class.md#open).

Drugie przeciążenie takie same działa tak, jakby używane pierwszy Konstruktor i natychmiast o nazwie [Dołącz](#attach) z tymi samymi parametrami. Zobacz `Attach` Aby uzyskać szczegółowe informacje.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#36](../../atl-mfc-shared/reference/codesnippet/cpp/cmemfile-class_1.cpp)]

##  <a name="detach"></a>  CMemFile::Detach

Wywołaj tę funkcję, aby uzyskać wskaźnik do bloku pamięci używany przez `CMemFile`.

```
BYTE* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do bloku pamięci, który zawiera zawartość pliku pamięci.

### <a name="remarks"></a>Uwagi

Podczas wywoływania tej funkcji również zamyka `CMemFile`. Możesz dołączyć bloku pamięci `CMemFile` przez wywołanie metody [Dołącz](#attach). Jeśli chcesz ponownie dołączyć plik i korzystać z danych w nim, należy wywołać [CFile::GetLength](../../mfc/reference/cfile-class.md#getlength) można pobrać długość pliku przed wywołaniem `Detach`. Należy pamiętać, że Jeśli dołączysz bloku pamięci `CMemFile` tak, aby jej dane mogą być używane ( `nGrowBytes` == 0), a następnie nie będzie można zwiększać pliku pamięci.

##  <a name="free"></a>  CMemFile::Free

Ta funkcja jest wywoływana `CMemFile` funkcji elementów członkowskich.

```
virtual void Free(BYTE* lpMem);
```

### <a name="parameters"></a>Parametry

*lpMem*<br/>
Wskaźnik do pamięci do przydzielenia.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę funkcję, aby zaimplementować niestandardowy pamięć dezalokacji. Jeśli zastąpisz tę funkcję, prawdopodobnie należy zastąpić [alokacji](#alloc) i [Realloc](#realloc) także.

##  <a name="growfile"></a>  CMemFile::GrowFile

Ta funkcja jest wywoływana przez kilka `CMemFile` funkcji elementów członkowskich.

```
virtual void GrowFile(SIZE_T dwNewLen);
```

### <a name="parameters"></a>Parametry

*dwNewLen*<br/>
Nowy rozmiar pliku pamięci.

### <a name="remarks"></a>Uwagi

Można go zastąpić, jeśli chcesz zmienić sposób `CMemFile` rozwoju jego pliku. Domyślna implementacja wywołuje [Realloc](#realloc) rośnie istniejącego bloku (lub [alokacji](#alloc) do utworzenia bloku pamięci), przydzielania pamięci w wielokrotnościach `nGrowBytes` wartość określona w konstruktorze lub [Dołącz](#attach) wywołania.

##  <a name="memcpy"></a>  CMemFile::Memcpy

Ta funkcja jest wywoływana `CMemFile` przesłonięć o [CFile::Read](../../mfc/reference/cfile-class.md#read) i [CFile::Write](../../mfc/reference/cfile-class.md#write) na przesyłanie danych do i z pliku pamięci.

```
virtual BYTE* Memcpy(
    BYTE* lpMemTarget,
    const BYTE* lpMemSource,
    SIZE_T nBytes);
```

### <a name="parameters"></a>Parametry

*lpMemTarget*<br/>
Wskaźnik do bloku pamięci, do którego zostaną skopiowane pamięci źródła.

*lpMemSource*<br/>
Wskaźnik do bloku pamięci źródłowego.

*nBytes*<br/>
Liczba bajtów do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Kopię *lpMemTarget*.

### <a name="remarks"></a>Uwagi

Przesłonić tę funkcję, jeśli chcesz zmienić sposób, `CMemFile` jest te kopie pamięci.

##  <a name="realloc"></a>  CMemFile::Realloc

Ta funkcja jest wywoływana `CMemFile` funkcji elementów członkowskich.

```
virtual BYTE* Realloc(
    BYTE* lpMem,
    SIZE_T nBytes);
```

### <a name="parameters"></a>Parametry

*lpMem*<br/>
Wskaźnik do bloku pamięci odbiorczego.

*nBytes*<br/>
Nowy rozmiar bloku pamięci.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do bloku pamięci, który został ponownie przydzielane (i prawdopodobnie przeniesiona), lub wartość NULL, jeśli ponowny przydział nie powiodła się.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę funkcję, aby zaimplementować ponownej alokacji pamięci niestandardowych. Jeśli zastąpisz tę funkcję, prawdopodobnie należy zastąpić [alokacji](#alloc) i [bezpłatna](#free) także.

## <a name="see-also"></a>Zobacz także

[Klasa CFile](../../mfc/reference/cfile-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
