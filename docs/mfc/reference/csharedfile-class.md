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
ms.openlocfilehash: c715ca1b8a2b647f89ada008f3c6606ca5e58783
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750391"
---
# <a name="csharedfile-class"></a>Klasa CSharedFile

[CMemFile](../../mfc/reference/cmemfile-class.md)-pochodna klasy, która obsługuje pliki pamięci współużytkowanej.

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
|[CSharedFile::Detach](#detach)|Zamyka plik pamięci współużytkowanej i zwraca dojście jego bloku pamięci.|
|[CSharedFile::SetHandle](#sethandle)|Dołącza plik pamięci współużytkowanej do bloku pamięci.|

## <a name="remarks"></a>Uwagi

Pliki pamięci zachowują się jak pliki dysków. Różnica polega na tym, że plik pamięci jest przechowywany w pamięci RAM, a nie na dysku. Plik pamięci jest przydatny do szybkiego przechowywania tymczasowego lub do przesyłania nieprzetworzonych bajtów lub szeregowanych obiektów między niezależnymi procesami.

Udostępnione pliki pamięci różnią się od innych plików pamięci w tej pamięci dla nich jest przydzielany z funkcji [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) Windows. Klasa `CSharedFile` przechowuje dane w globalnie przydzielonym bloku pamięci (utworzonym przy użyciu), `GlobalAlloc`a ten blok pamięci może być współużytkowany przy użyciu DDE, Schowka lub innych jednolitych operacji transferu danych OLE/COM, na przykład za pomocą `IDataObject`.

`GlobalAlloc`zwraca uchwyt HGLOBAL, a nie wskaźnik do pamięci, takich jak wskaźnik zwrócony przez [malloc](../../c-runtime-library/reference/malloc.md). Uchwyt HGLOBAL jest potrzebny w niektórych zastosowaniach. Na przykład, aby umieścić dane w Schowku, potrzebujesz uchwytu HGLOBAL.

`CSharedFile`nie używa plików mapowanych w pamięci, a dane nie mogą być bezpośrednio współużytkowane między procesami.

`CSharedFile`obiekty mogą automatycznie przydzielać własną pamięć. Można też dołączyć własny blok pamięci `CSharedFile` do obiektu, wywołując [CSharedFile::SetHandle](#sethandle). W obu przypadkach pamięć do powiększania pliku pamięci `nGrowBytes`jest przydzielana `nGrowBytes` w przyrostach o rozmiarze, jeśli nie jest zero.

Aby uzyskać więcej informacji, zobacz artykuł [Pliki w MFC](../../mfc/files-in-mfc.md) i [Obsługa plików](../../c-runtime-library/file-handling.md) w *odwołaniu do biblioteki w czasie wykonywania*.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cfile](../../mfc/reference/cfile-class.md)

[Cmemfile](../../mfc/reference/cmemfile-class.md)

`CSharedFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxadv.h

## <a name="csharedfilecsharedfile"></a><a name="csharedfile"></a>CSharedFile::CSharedFile

Konstruuje `CSharedFile` obiekt i przydziela dla niego pamięć.

```
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,
    UINT nGrowBytes = 4096);
```

### <a name="parameters"></a>Parametry

*nAllocFlags*<br/>
Flagi wskazujące sposób przydzielania pamięci. Zobacz [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) listę prawidłowych wartości flag.

*nGrowBytes ( nGrowBytes )*<br/>
Przyrost alokacji pamięci w bajtach.

## <a name="csharedfiledetach"></a><a name="detach"></a>CSharedFile::Detach

Wywołanie tej funkcji, aby zamknąć plik pamięci i odłączyć go od bloku pamięci.

```
HGLOBAL Detach();
```

### <a name="return-value"></a>Wartość zwracana

Dojście bloku pamięci zawierającego zawartość pliku pamięci.

### <a name="remarks"></a>Uwagi

Można go ponownie otworzyć, wywołując [SetHandle](#sethandle), używając uchwytu zwróconego przez **Detach**.

## <a name="csharedfilesethandle"></a><a name="sethandle"></a>CSharedFile::SetHandle

Wywołanie tej funkcji, aby dołączyć `CSharedFile` blok pamięci globalnej do obiektu.

```cpp
void SetHandle(
    HGLOBAL hGlobalMemory,
    BOOL bAllowGrow = TRUE);
```

### <a name="parameters"></a>Parametry

*hGlobalMemory*<br/>
Uchwyt do pamięci globalnej, który `CSharedFile`ma być dołączony do pliku .

*bAllowGrow (Niewola)*<br/>
Określa, czy blok pamięci może rosnąć.

### <a name="remarks"></a>Uwagi

Jeśli *bAllowGrow* jest niezerowy, rozmiar bloku pamięci jest zwiększany w razie potrzeby, na przykład, jeśli spróbujesz zapisać więcej bajtów do pliku niż rozmiar bloku pamięci.

## <a name="see-also"></a>Zobacz też

[Klasa CMemFile](../../mfc/reference/cmemfile-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CMemFile](../../mfc/reference/cmemfile-class.md)
