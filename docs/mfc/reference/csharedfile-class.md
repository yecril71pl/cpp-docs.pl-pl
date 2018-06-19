---
title: Klasa CSharedFile | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSharedFile
- AFXADV/CSharedFile
- AFXADV/CSharedFile::CSharedFile
- AFXADV/CSharedFile::Detach
- AFXADV/CSharedFile::SetHandle
dev_langs:
- C++
helpviewer_keywords:
- CSharedFile [MFC], CSharedFile
- CSharedFile [MFC], Detach
- CSharedFile [MFC], SetHandle
ms.assetid: 5d000422-9ede-4318-a8c9-f7412b674f39
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bee22940fb197d480f4ae3550d8dd59780c256b5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370184"
---
# <a name="csharedfile-class"></a>Klasa CSharedFile
[CMemFile](../../mfc/reference/cmemfile-class.md)-klasy pochodnej, która obsługuje udostępnionych plików pamięci.  
  
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
|[CSharedFile::Detach](#detach)|Zamyka pliku pamięci współużytkowanej i zwraca dojście jego blok pamięci.|  
|[CSharedFile::SetHandle](#sethandle)|Dołącza pliku pamięci współużytkowanej do bloku pamięci.|  
  
## <a name="remarks"></a>Uwagi  
 Pliki pamięci przypominają plików na dysku, z wyjątkiem tego, że plik jest przechowywany w pamięci RAM, a nie na dysku. Pliku pamięci jest przydatne do szybkiego tymczasowego przechowywania lub przesyłania bajtów raw lub serializować obiektów między procesami niezależne.  
  
 Pliki pamięci współużytkowanej różnią się od innych plików pamięci jest przydzielana pamięć dla nich, z [działanie funkcji GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) funkcji systemu Windows. `CSharedFile` Klasy przechowuje dane w bloku globalnie alokacji pamięci (utworzone za pomocą **działanie funkcji GlobalAlloc**), a ten blok pamięci może być udostępniony przy użyciu DDE, Schowek lub innych OLE/COM uniform operacji transferu danych, na przykład przy użyciu `IDataObject`.  
  
 **Działanie funkcji GlobalAlloc** zwraca `HGLOBAL` obsługi zamiast wskaźnik do pamięci, takich jak zwrócony przez wskaźnik [— funkcja malloc](../../c-runtime-library/reference/malloc.md). `HGLOBAL` Dojścia jest niezbędne w niektórych aplikacjach. Na przykład umieszczanie danych w Schowku należy `HGLOBAL` obsługi.  
  
 Należy pamiętać, że `CSharedFile` nie nie używaj mapowanych na pamięć plików i danych nie można udostępnić bezpośrednio między procesami.  
  
 `CSharedFile` obiekty automatycznie można przydzielić pamięci własnych lub można dołączać własne bloku pamięci `CSharedFile` obiektu przez wywołanie metody [CSharedFile::SetHandle](#sethandle). W obu przypadkach jest przydzielana pamięć dla automatycznie powiększania pliku pamięci w `nGrowBytes`-o rozmiarze zwiększa, jeśli `nGrowBytes` nie jest równa zero.  
  
 Aby uzyskać więcej informacji, zobacz artykuł [pliki w MFC](../../mfc/files-in-mfc.md) i [Obsługa plików](../../c-runtime-library/file-handling.md) w *odwołanie do biblioteki wykonawczej*.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cfile —](../../mfc/reference/cfile-class.md)  
  
 [CMemFile](../../mfc/reference/cmemfile-class.md)  
  
 `CSharedFile`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxadv.h  
  
##  <a name="csharedfile"></a>  CSharedFile::CSharedFile  
 Konstruuje `CSharedFile` obiektu i przydziela pamięć.  
  
```  
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,  
    UINT nGrowBytes = 4096);
```  
  
### <a name="parameters"></a>Parametry  
 *nAllocFlags*  
 Flagi wskazującą, jaki jest pamięci do przydzielenia. Zobacz [działanie funkcji GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) listę prawidłowych wartości flag.  
  
 `nGrowBytes`  
 Przyrost alokacji pamięci w bajtach.  
  
##  <a name="detach"></a>  CSharedFile::Detach  
 Wywołanie tej funkcji, aby zamknąć plik pamięci i ją odłączyć od bloku pamięci.  
  
```  
HGLOBAL Detach();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście blok pamięci, która zawiera zawartość pliku pamięci.  
  
### <a name="remarks"></a>Uwagi  
 Możesz uruchomić go przez wywołanie metody [SetHandle](#sethandle), przy użyciu dojścia zwrócony przez **Detach**.  
  
##  <a name="sethandle"></a>  CSharedFile::SetHandle  
 Wywołanie tej funkcji można dołączyć blok pamięci globalnej do `CSharedFile` obiektu.  
  
```  
void SetHandle(
    HGLOBAL hGlobalMemory,  
    BOOL bAllowGrow = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *hGlobalMemory*  
 Dojście do globalnej pamięci jest dołączony do `CSharedFile`.  
  
 `bAllowGrow`  
 Określa, czy blok pamięci może wzrosnąć.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `bAllowGrow` różną od zera, rozmiaru bloku pamięci zwiększa się zgodnie z potrzebami, na przykład, jeśli próba dokonania do większej liczby bajtów do zapisu pliku niż przydzielonych dla bloku pamięci.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CMemFile](../../mfc/reference/cmemfile-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CMemFile](../../mfc/reference/cmemfile-class.md)
