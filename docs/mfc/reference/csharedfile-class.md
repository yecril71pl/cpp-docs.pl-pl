---
title: Klasa CSharedFile
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
ms.openlocfilehash: 74a34ec169868d3e28f78f33da38dbda21ef23b3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502613"
---
# <a name="csharedfile-class"></a>Klasa CSharedFile

Klasa pochodna [CMemFile](../../mfc/reference/cmemfile-class.md), która obsługuje pliki pamięci współdzielonej.

## <a name="syntax"></a>Składnia

```
class CSharedFile : public CMemFile
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSharedFile::CSharedFile](#csharedfile)|Konstruuje `CSharedFile` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSharedFile::Detach](#detach)|Zamyka plik pamięci współużytkowanej i zwraca uchwyt jego bloku pamięci.|
|[CSharedFile::SetHandle](#sethandle)|Dołącza plik pamięci współdzielonej do bloku pamięci.|

## <a name="remarks"></a>Uwagi

Pliki pamięci zachowują się jak pliki dysków. Różnica polega na tym, że plik pamięci jest przechowywany w pamięci RAM, a nie na dysku. Plik pamięci jest przydatny do szybkiego magazynu tymczasowego lub do przesyłania nieprzetworzonych bajtów lub serializowanych obiektów między procesami niezależnymi.

Pliki pamięci współdzielonej różnią się od innych plików pamięci w tej pamięci do przydzielenia przy użyciu funkcji [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) systemu Windows. Klasa przechowuje dane w globalnie przydzielonym bloku pamięci (utworzonym `GlobalAlloc`za pomocą), a ten blok pamięci może być współużytkowany przy użyciu DDE, Schowka lub innych operacji jednolitego transferu danych OLE/com, na przykład przy `IDataObject`użyciu. `CSharedFile`

`GlobalAlloc`Zwraca uchwyt HGLOBAL, a nie wskaźnik do pamięci, taki jak wskaźnik zwrócony przez [malloc](../../c-runtime-library/reference/malloc.md). W niektórych aplikacjach jest wymagany uchwyt HGLOBAL. Na przykład, aby umieścić dane w schowku, potrzebujesz uchwytu HGLOBAL.

`CSharedFile`nie używa plików mapowanych w pamięci, a dane nie mogą być bezpośrednio udostępniane między procesami.

`CSharedFile`obiekty mogą automatycznie przydzielać własne pamięci. Lub można dołączyć własny blok pamięci do `CSharedFile` obiektu przez wywołanie [CSharedFile:: SetHandle](#sethandle). W obu przypadkach pamięć służąca do zwiększania rozmiaru pliku pamięci jest automatycznie `nGrowBytes`alokowana, jeśli `nGrowBytes` nie jest równa zero.

Aby uzyskać więcej informacji, zobacz [pliki artykułów w MFC](../../mfc/files-in-mfc.md) i [Obsługa plików](../../c-runtime-library/file-handling.md) w *dokumentacji dotyczącej biblioteki wykonawczej*.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CMemFile](../../mfc/reference/cmemfile-class.md)

`CSharedFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxadv. h

##  <a name="csharedfile"></a>CSharedFile::CSharedFile

Konstruuje `CSharedFile` obiekt i przydziela do niego pamięć.

```
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,
    UINT nGrowBytes = 4096);
```

### <a name="parameters"></a>Parametry

*nAllocFlags*<br/>
Flagi wskazujące sposób przydzielenia pamięci. Zobacz [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) , aby uzyskać listę prawidłowych wartości flag.

*nGrowBytes*<br/>
Przyrost alokacji pamięci w bajtach.

##  <a name="detach"></a>CSharedFile::D etach

Wywołaj tę funkcję, aby zamknąć plik pamięci i odłączyć go od bloku pamięci.

```
HGLOBAL Detach();
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt bloku pamięci, który zawiera zawartość pliku pamięci.

### <a name="remarks"></a>Uwagi

Możesz otworzyć go ponownie, wywołując metodę [SetHandle](#sethandle)przy użyciu dojścia zwróconego przez **Odłącz**.

##  <a name="sethandle"></a>CSharedFile:: SetHandle

Wywołaj tę funkcję, aby dołączyć blok pamięci globalnej do `CSharedFile` obiektu.

```
void SetHandle(
    HGLOBAL hGlobalMemory,
    BOOL bAllowGrow = TRUE);
```

### <a name="parameters"></a>Parametry

*hGlobalMemory*<br/>
Dojście do pamięci globalnej, która ma zostać dołączona do programu `CSharedFile`.

*bAllowGrow*<br/>
Określa, czy blok pamięci może zostać powiększony.

### <a name="remarks"></a>Uwagi

Jeśli *bAllowGrow* ma wartość różną od zera, rozmiar bloku pamięci jest zwiększany w miarę potrzeb, na przykład w przypadku próby zapisania większej liczby bajtów do pliku niż rozmiar bloku pamięci.

## <a name="see-also"></a>Zobacz także

[Klasa CMemFile](../../mfc/reference/cmemfile-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CMemFile](../../mfc/reference/cmemfile-class.md)
