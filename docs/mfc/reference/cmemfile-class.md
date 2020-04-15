---
title: Klasa CMemFile
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
ms.openlocfilehash: 46937795499fd9f697f9778c263a1ee011777c0d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370020"
---
# <a name="cmemfile-class"></a>Klasa CMemFile

[CFile](../../mfc/reference/cfile-class.md)-pochodna klasy, która obsługuje pliki pamięci.

## <a name="syntax"></a>Składnia

```
class CMemFile : public CFile
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Plik CMem::CMemFile](#cmemfile)|Tworzy obiekt pliku pamięci.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Plik CMem: dołączanie](#attach)|Dołącza blok pamięci do `CMemFile`pliku .|
|[CMemFile::Detach](#detach)|Odłącza blok pamięci `CMemFile` i zwraca wskaźnik do bloku odłączony.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[Plik CMem::Alloc](#alloc)|Zastąd, aby zmodyfikować zachowanie alokacji pamięci.|
|[CMemFile::Wolny](#free)|Zastąd, aby zmodyfikować zachowanie alokacji pamięci.|
|[Plik CMem::Plik Grow](#growfile)|Zastąp, aby zmodyfikować zachowanie podczas powiększania pliku.|
|[CMemFile::Memcpy](#memcpy)|Zastąp, aby zmodyfikować zachowanie kopiowania pamięci podczas odczytywania i zapisywania plików.|
|[CMemFile::Realloc](#realloc)|Zastąd, aby zmodyfikować zachowanie ponownego przydziału pamięci.|

## <a name="remarks"></a>Uwagi

Te pliki pamięci zachowują się jak pliki dysków, z tą różnicą, że plik jest przechowywany w pamięci RAM, a nie na dysku. Plik pamięci jest przydatny do szybkiego przechowywania tymczasowego lub do przesyłania nieprzetworzonych bajtów lub szeregowanych obiektów między niezależnymi procesami.

`CMemFile`obiekty mogą automatycznie przydzielić własną pamięć lub można dołączyć `CMemFile` własny blok pamięci do obiektu, wywołując [Attach](#attach). W obu przypadkach pamięć do powiększania pliku pamięci `nGrowBytes`jest przydzielana `nGrowBytes` w przyrostach o rozmiarze, jeśli nie jest równa zero.

Blok pamięci zostanie automatycznie usunięty po `CMemFile` zniszczeniu obiektu, jeśli pamięć `CMemFile` została pierwotnie przydzielona przez obiekt; w przeciwnym razie użytkownik jest odpowiedzialny za przydzielenie pamięci dołączonej do obiektu.

Dostęp do bloku pamięci można uzyskać za pomocą wskaźnika dostarczonego podczas odłączyć go od `CMemFile` obiektu, wywołując [Detach](#detach).

Najczęstszym zastosowaniem `CMemFile` jest utworzenie `CMemFile` obiektu i użycie go przez wywołanie funkcji elementów członkowskich [CFile.](../../mfc/reference/cfile-class.md) Należy zauważyć, `CMemFile` że utworzenie automatycznie otwiera go: nie wywołujesz [CFile::Open](../../mfc/reference/cfile-class.md#open), który jest używany tylko dla plików dyskowych. Ponieważ `CMemFile` nie używa pliku dysku, element `CFile::m_hFile` członkowski danych nie jest używany.

Funkcje `CFile` członkowskie [Duplicate](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange)i [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) nie są implementowane dla `CMemFile`. Jeśli wywołasz te `CMemFile` funkcje na obiekcie, otrzymasz [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

`CMemFile`korzysta z funkcji biblioteki w czasie wykonywania [malloc](../../c-runtime-library/reference/malloc.md), [realloc](../../c-runtime-library/reference/realloc.md)i [swobodnie](../../c-runtime-library/reference/free.md) przydzielać, ponownie przydzielać i przydzielać pamięć; i wewnętrznej [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md) do blokowania pamięci kopii podczas czytania i pisania. Jeśli chcesz zmienić to zachowanie lub `CMemFile` zachowanie, gdy powiększa plik, wywodź własną klasę z `CMemFile` i zastąpić odpowiednie funkcje.

Aby uzyskać `CMemFile`więcej informacji na temat , zobacz artykuły [Pliki w MFC](../../mfc/files-in-mfc.md) i [zarządzanie pamięcią (MFC)](../../mfc/memory-management.md) i zobacz [Obsługa plików](../../c-runtime-library/file-handling.md) w *odwołaniu do biblioteki w czasie wykonywania*.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cfile](../../mfc/reference/cfile-class.md)

`CMemFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="cmemfilealloc"></a><a name="alloc"></a>Plik CMem::Alloc

Ta funkcja jest `CMemFile` wywoływana przez funkcje członkowskie.

```
virtual BYTE* Alloc(SIZE_T nBytes);
```

### <a name="parameters"></a>Parametry

*n Bajty*<br/>
Liczba bajtów pamięci do przydzielenia.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do przydzielonego bloku pamięci lub null, jeśli alokacja nie powiodła się.

### <a name="remarks"></a>Uwagi

Zastąd w tej funkcji zaimplementuj alokację pamięci niestandardowej. Jeśli zastąpisz tę funkcję, prawdopodobnie będziesz chciał zastąpić [Free](#free) i [Realloc,](#realloc) jak również.

Domyślna implementacja używa funkcji biblioteki wykonawczej [malloc](../../c-runtime-library/reference/malloc.md) do przydzielenia pamięci.

## <a name="cmemfileattach"></a><a name="attach"></a>Plik CMem: dołączanie

Wywołanie tej funkcji, aby `CMemFile`dołączyć blok pamięci do .

```
void Attach(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>Parametry

*lpBuffer (lpBuffer)*<br/>
Wskaźnik do buforu, który `CMemFile`ma być dołączony do .

*nBufferSize (Rozmiar)*<br/>
Liczba całkowita określająca rozmiar buforu w bajtach.

*nGrowBytes ( nGrowBytes )*<br/>
Przyrost alokacji pamięci w bajtach.

### <a name="remarks"></a>Uwagi

Powoduje `CMemFile` to użycie bloku pamięci jako pliku pamięci.

Jeśli *nGrowBytes* jest `CMemFile` 0, ustawi długość pliku na *nBufferSize*. Oznacza to, że dane w bloku pamięci `CMemFile` przed jego dołączeniem będą używane jako plik. Pliki pamięci utworzone w ten sposób nie mogą być uprawiane.

Ponieważ plik nie może być uprawiany, należy uważać, aby nie spowodować, aby spróbować `CMemFile` rozwijać plik. Na przykład nie wywoływać `CMemFile` zastąpienia [CFile:Write](../../mfc/reference/cfile-class.md#write) napisać poza koniec lub nie wywołać [CFile:SetLength](../../mfc/reference/cfile-class.md#setlength) o długości dłuższej niż *nBufferSize*.

Jeśli *nGrowBytes* jest większa `CMemFile` niż 0, zignoruje zawartość dołączonego bloku pamięci. Będziesz musiał zapisać zawartość pliku pamięci od podstaw `CMemFile` za pomocą `CFile::Write`zastąpienia . Jeśli spróbujesz napisać poza koniec pliku lub zwiększyć `CMemFile` plik, wywołując `CFile::SetLength` `CMemFile` zastąpienie , zwiększy alokacji pamięci w przyrostach *nGrowBytes*. Zwiększenie alokacji pamięci zakończy się niepowodzeniem, jeśli blok pamięci, do `Attach` którego przechodzisz, nie został przydzielony przy pomocą metody zgodnej z [alloc](#alloc). Aby być zgodnym z `Alloc`domyślną implementacją programu , należy przydzielić pamięć za pomocą funkcji biblioteki wykonawczej [malloc](../../c-runtime-library/reference/malloc.md) lub [calloc](../../c-runtime-library/reference/calloc.md).

## <a name="cmemfilecmemfile"></a><a name="cmemfile"></a>Plik CMem::CMemFile

Pierwsze przeciążenie otwiera pusty plik pamięci.

```
CMemFile(UINT nGrowBytes = 1024);

CMemFile(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>Parametry

*nGrowBytes ( nGrowBytes )*<br/>
Przyrost alokacji pamięci w bajtach.

*lpBuffe*r Wskaźnik do buforu, który odbiera informacje o rozmiarze *nBufferSize*.

*nBufferSize (Rozmiar)*<br/>
Liczba całkowita określająca rozmiar buforu plików w bajtach.

### <a name="remarks"></a>Uwagi

Należy zauważyć, że plik jest otwierany przez konstruktora i że nie należy wywoływać [CFile::Open](../../mfc/reference/cfile-class.md#open).

Drugie przeciążenie działa tak samo, jak w przypadku użycia pierwszego konstruktora i natychmiast [wywołane Dołącz](#attach) z tych samych parametrów. Aby uzyskać szczegółowe informacje, zobacz opis funkcji `Attach`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#36](../../atl-mfc-shared/reference/codesnippet/cpp/cmemfile-class_1.cpp)]

## <a name="cmemfiledetach"></a><a name="detach"></a>CMemFile::Detach

Wywołanie tej funkcji, aby uzyskać wskaźnik `CMemFile`do bloku pamięci używanego przez program .

```
BYTE* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do bloku pamięci, który zawiera zawartość pliku pamięci.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji `CMemFile`powoduje również zamknięcie pliku . Do bloku `CMemFile` pamięci można ponownie dołączyć, wywołując [dołącz](#attach). Jeśli chcesz ponownie dołączyć plik i użyć danych w nim, należy wywołać [CFile::GetLength,](../../mfc/reference/cfile-class.md#getlength) `Detach`aby uzyskać długość pliku przed wywołaniem . Należy zauważyć, że jeśli `CMemFile` dołączysz blok pamięci, `nGrowBytes` aby można było użyć jego danych ( == 0), nie będzie można zwiększyć pliku pamięci.

## <a name="cmemfilefree"></a><a name="free"></a>CMemFile::Wolny

Ta funkcja jest `CMemFile` wywoływana przez funkcje członkowskie.

```
virtual void Free(BYTE* lpMem);
```

### <a name="parameters"></a>Parametry

*lpMem (właso)*<br/>
Wskaźnik do pamięci, która ma zostać cofnięta.

### <a name="remarks"></a>Uwagi

Zastąd w tej funkcji zaimplementuj niestandardową alokację pamięci. Jeśli zastąpisz tę funkcję, prawdopodobnie będziesz chciał zastąpić [alloc](#alloc) i [realokacji,](#realloc) jak również.

## <a name="cmemfilegrowfile"></a><a name="growfile"></a>Plik CMem::Plik Grow

Ta funkcja jest wywoływana `CMemFile` przez kilka funkcji członkowskich.

```
virtual void GrowFile(SIZE_T dwNewLen);
```

### <a name="parameters"></a>Parametry

*dwNewLen (Nienawisłe*<br/>
Nowy rozmiar pliku pamięci.

### <a name="remarks"></a>Uwagi

Można go zastąpić, jeśli chcesz zmienić sposób `CMemFile` powiększania jego pliku. Domyślna implementacja wywołuje [Realloc](#realloc) rozwijać istniejący blok (lub [Alloc](#alloc) utworzyć blok pamięci), przydzielanie pamięci w wielokrotności `nGrowBytes` wartości określonej w konstruktorze lub [Dołącz](#attach) wywołanie.

## <a name="cmemfilememcpy"></a><a name="memcpy"></a>CMemFile::Memcpy

Ta funkcja jest `CMemFile` wywoływana przez zastąpienia [CFile::Read](../../mfc/reference/cfile-class.md#read) i [CFile::Write](../../mfc/reference/cfile-class.md#write) do przesyłania danych do i z pliku pamięci.

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

*n Bajty*<br/>
Liczba bajtów do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Kopia *lpMemTarget*.

### <a name="remarks"></a>Uwagi

Zastąd w tej funkcji należy `CMemFile` zmienić sposób kopiowania pamięci.

## <a name="cmemfilerealloc"></a><a name="realloc"></a>CMemFile::Realloc

Ta funkcja jest `CMemFile` wywoływana przez funkcje członkowskie.

```
virtual BYTE* Realloc(
    BYTE* lpMem,
    SIZE_T nBytes);
```

### <a name="parameters"></a>Parametry

*lpMem (właso)*<br/>
Wskaźnik do bloku pamięci do ponownego przydzielenia.

*n Bajty*<br/>
Nowy rozmiar bloku pamięci.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do bloku pamięci, który został ponownie przydzielony (i ewentualnie przeniesiony) lub NULL, jeśli ponowne przydzielenie nie powiodło się.

### <a name="remarks"></a>Uwagi

Zastąd w tej funkcji zaimplementuj ponowną alokację pamięci niestandardowej. Jeśli zastąpisz tę funkcję, prawdopodobnie będziesz chciał zastąpić [alloc](#alloc) i [free,](#free) jak również.

## <a name="see-also"></a>Zobacz też

[Klasa CFile](../../mfc/reference/cfile-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
