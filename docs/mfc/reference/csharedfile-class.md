---
title: CSharedFile Class
ms.date: 11/04/2016
f1_keywords:
- CSharedFile
- AFXADV/CSharedFile
- AFXADV/CSharedFile::CSharedFile
- AFXADV/CSharedFile::Detach
- AFXADV/CSharedFile::SetHandle
helpviewer_keywords:
- CSharedFile [MFC], CSharedFile
- CSharedFile [MFC], Detach
- CSharedFile [MFC], SetHandle
ms.assetid: 5d000422-9ede-4318-a8c9-f7412b674f39
ms.openlocfilehash: 0a9bbf3072a665c04501025d421839fa90a37225
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344420"
---
# <a name="csharedfile-class"></a>CSharedFile Class

[CMemFile](../../mfc/reference/cmemfile-class.md)-klasy pochodnej, który obsługuje współdzielone pliki w pamięci.

## <a name="syntax"></a>Składnia

```
class CSharedFile : public CMemFile
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSharedFile::CSharedFile](#csharedfile)|Konstruuje `CSharedFile` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSharedFile::Detach](#detach)|Zamyka pliku pamięci współużytkowanej i zwraca uchwyt jego bloku pamięci.|
|[CSharedFile::SetHandle](#sethandle)|Dołącza pliku pamięci współużytkowanej do bloku pamięci.|

## <a name="remarks"></a>Uwagi

Pliki pamięci zachowują się jak plików na dysku. Różnica polega na tym, plik pamięci są przechowywane w pamięci RAM, a nie na dysku. Plik pamięci jest przydatne do błyskawicznie obsługiwany magazyn tymczasowy lub transferu bajtów raw lub serializacji obiektów między procesami, niezależnie od.

Pliki pamięci współużytkowanej różnią się od innych plików pamięci w tym, że pamięć dla nich została przydzielona z [działanie funkcji GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc) funkcji Windows. `CSharedFile` Klasa przechowuje dane w bloku globalnie alokacji pamięci (utworzone za pomocą `GlobalAlloc`), a ten blok pamięci mogą być udostępniane za pomocą DDE, Schowek lub innych OLE/COM jednolitego operacji transferu danych, na przykład za pomocą `IDataObject`.

`GlobalAlloc` Zwraca wartości HGLOBAL obsługi, a nie wskaźnik do pamięci, takich jak wskaźnik zwracany przez [— funkcja malloc](../../c-runtime-library/reference/malloc.md). Uchwyt wartości HGLOBAL jest wymagana w określonych aplikacji. Na przykład umieszczenie danych w Schowku należy wartości HGLOBAL dojście.

`CSharedFile` Nie używaj plików zamapowanych w pamięci i danych nie można bezpośrednio współużytkować między procesami.

`CSharedFile` obiekty może automatycznie przydzielać własne pamięci. Lub możesz dołączyć własnego bloku pamięci `CSharedFile` obiektu przez wywołanie metody [CSharedFile::SetHandle](#sethandle). W obu przypadkach pamięci dla automatycznego powiększania pliku pamięci są przydzielane w `nGrowBytes`-o rozmiarze co, jeśli `nGrowBytes` nie ma wartość zero.

Aby uzyskać więcej informacji, zobacz artykuł [pliki w MFC](../../mfc/files-in-mfc.md) i [Obsługa plików](../../c-runtime-library/file-handling.md) w *odwołanie do biblioteki wykonawczej*.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CMemFile](../../mfc/reference/cmemfile-class.md)

`CSharedFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxadv.h

##  <a name="csharedfile"></a>  CSharedFile::CSharedFile

Konstruuje `CSharedFile` obiektu i przydziela mu pamięć.

```
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,
    UINT nGrowBytes = 4096);
```

### <a name="parameters"></a>Parametry

*nAllocFlags*<br/>
Flagi wskazujące, jak jest pamięci do przydzielenia. Zobacz [działanie funkcji GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc) listę prawidłowych wartości flag.

*nGrowBytes*<br/>
Zwiększenie przydziału pamięci w bajtach.

##  <a name="detach"></a>  CSharedFile::Detach

Wywołaj tę funkcję, aby zamknąć plik pamięci i odłączania bloku pamięci.

```
HGLOBAL Detach();
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt bloku pamięci, który zawiera zawartość pliku pamięci.

### <a name="remarks"></a>Uwagi

Możesz uruchomić go przez wywołanie metody [SetHandle](#sethandle), za pomocą uchwyt zwracany przez **Odłącz**.

##  <a name="sethandle"></a>  CSharedFile::SetHandle

Wywołaj tę funkcję, aby dołączyć blok pamięci globalnej do `CSharedFile` obiektu.

```
void SetHandle(
    HGLOBAL hGlobalMemory,
    BOOL bAllowGrow = TRUE);
```

### <a name="parameters"></a>Parametry

*hGlobalMemory*<br/>
Dojście do pamięci globalnej do podłączenia do `CSharedFile`.

*bAllowGrow*<br/>
Określa, czy blok pamięci może wzrosnąć.

### <a name="remarks"></a>Uwagi

Jeśli *bAllowGrow* jest różna od zera, rozmiar bloku pamięci zwiększa się zgodnie z potrzebami, na przykład, jeśli użytkownik podejmie próbę zapisu większą liczbę bajtów w pliku niż rozmiar bloku pamięci.

## <a name="see-also"></a>Zobacz także

[Klasa CMemFile](../../mfc/reference/cmemfile-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CMemFile](../../mfc/reference/cmemfile-class.md)
