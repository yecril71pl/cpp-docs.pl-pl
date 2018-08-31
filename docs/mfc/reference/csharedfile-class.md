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
ms.openlocfilehash: 38267ed5755b99bd97e4c923611d297673fcc41e
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43215586"
---
# <a name="csharedfile-class"></a>Klasa CSharedFile
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
 Pliki pamięci zachowują się jak plików na dysku, z tą różnicą, że plik jest przechowywany w pamięci RAM, a nie na dysku. Plik pamięci jest przydatna, błyskawicznie obsługiwany magazyn tymczasowy lub transferu bajtów raw lub serializacji obiektów między procesami niezależne.  
  
 Pliki pamięci współużytkowanej różnią się od innych plików pamięci w tym, że pamięć dla nich została przydzielona z [działanie funkcji GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc) funkcji Windows. `CSharedFile` Klasa przechowuje dane w bloku globalnie alokacji pamięci (utworzone za pomocą `GlobalAlloc`), a ten blok pamięci mogą być udostępniane za pomocą DDE, Schowek lub innych OLE/COM jednolitego operacji transferu danych, na przykład za pomocą `IDataObject`.  
  
 `GlobalAlloc` Zwraca wartości HGLOBAL obsługi, a nie wskaźnik do pamięci, takich jak wskaźnik zwracany przez [— funkcja malloc](../../c-runtime-library/reference/malloc.md). Uchwyt wartości HGLOBAL jest wymagana w określonych aplikacji. Na przykład umieszczenie danych w Schowku należy wartości HGLOBAL dojście.  
  
 Należy pamiętać, że `CSharedFile` nie nie Użyj mapowane w pamięci plików i danych nie może być współużytkowana bezpośrednio między procesami.  
  
 `CSharedFile` obiekty może automatycznie przydzielać własne pamięci lub możesz dołączyć własnego bloku pamięci `CSharedFile` obiektu przez wywołanie metody [CSharedFile::SetHandle](#sethandle). W obu przypadkach pamięci dla automatycznego powiększania pliku pamięci są przydzielane w `nGrowBytes`-o rozmiarze co, jeśli `nGrowBytes` nie jest równa zero.  
  
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
 *nAllocFlags*  
 Flagi wskazujące, jak jest pamięci do przydzielenia. Zobacz [działanie funkcji GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc) listę prawidłowych wartości flag.  
  
 *nGrowBytes*  
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
 *hGlobalMemory*  
 Dojście do pamięci globalnej do podłączenia do `CSharedFile`.  
  
 *bAllowGrow*  
 Określa, czy blok pamięci może wzrosnąć.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli *bAllowGrow* zostanie wartość różną od zera, rozmiar bloku pamięci zwiększa się zgodnie z potrzebami, na przykład, jeśli próba zostanie podjęta zapisu większą liczbę bajtów w pliku nie została przydzielona do bloku pamięci.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CMemFile](../../mfc/reference/cmemfile-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CMemFile](../../mfc/reference/cmemfile-class.md)
