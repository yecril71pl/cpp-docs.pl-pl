---
title: IAtlStringMgr, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- IAtlStringMgr
- ATLSIMPSTR/ATL::IAtlStringMgr
- ATLSIMPSTR/ATL::Allocate
- ATLSIMPSTR/ATL::Clone
- ATLSIMPSTR/ATL::Free
- ATLSIMPSTR/ATL::GetNilString
- ATLSIMPSTR/ATL::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- shared classes, IAtlStringMgr
- memory, managing
- IAtlStringMgr class
ms.assetid: 722f0346-a770-4aa7-8f94-177be8dba823
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a69b2667b92b27f7310bbc70087331acd4aefaa5
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37880651"
---
# <a name="iatlstringmgr-class"></a>IAtlStringMgr, klasa
Ta klasa reprezentuje interfejs służący do `CStringT` Menedżer pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```
__interface IAtlStringMgr
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Przydziel](#allocate)|Wywołaj tę metodę można przydzielić nowej struktury danych ciągu.|  
|[Klon](#clone)|Wywołaj tę metodę, aby zwrócić wskaźnik do nowego Menedżera ciąg do użycia z innego wystąpienia programu `CSimpleStringT`.|  
|[Bezpłatne](#free)|Wywołaj tę metodę, aby zwolnić struktury danych ciągu.|  
|[GetNilString](#getnilstring)|Zwraca wskaźnik do `CStringData` obiekt używany przez obiekty pusty ciąg.|  
|[Ponowne przydzielenie](#reallocate)|Wywołaj tę metodę w celu ponownego przydzielenia struktury danych ciągu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs zarządza pamięci używane przez klasy ciągu niezależne od MFC; takie jak [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), [CStringT](../../atl-mfc-shared/reference/cstringt-class.md), i [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md).  
  
 Ta klasa umożliwia również zaimplementować Menedżera pamięci niestandardowe dla swojej klasy niestandardowy ciąg. Aby uzyskać więcej informacji, zobacz [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsimpstr.h  
  
##  <a name="allocate"></a>  IAtlStringMgr::Allocate  
 Przydziela nową strukturę danych ciągu.  
  
```
CStringData* Allocate(int nAllocLength,int nCharSize) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *nAllocLength*  
 Liczba znaków w nowy blok pamięci.  
  
 *nCharSize*  
 Rozmiar (w bajtach) to typ znaku używany przez Menedżera ciągów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do bloku pamięci nowo przydzielone.  
  
> [!NOTE]
>  Sygnalizuje błąd alokacji, zostanie zgłoszony wyjątek. Zamiast tego błąd alokacji powinny być zasygnalizowany, zwracając wartość NULL.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj [IAtlStringMgr::Free](#free) lub [IAtlStringMgr::ReAllocate](#reallocate) zwolnienie pamięci przydzielonej przez tę metodę.  
  
> [!NOTE]
>  Aby uzyskać przykłady użycia, zobacz [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
##  <a name="clone"></a>  IAtlStringMgr::Clone  
 Zwraca wskaźnik do nowego Menedżera ciąg do użycia z innego wystąpienia programu `CSimpleStringT`.  
  
```
IAtlStringMgr* Clone() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca kopię obiektu `IAtlStringMgr` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Często wywoływane przez platformę, gdy Menedżera ciągów jest wymagany w przypadku nowego ciągu. W większości przypadków **to** wskaźnik jest zwracany.  
  
 Jednak jeśli Menedżer pamięci nie obsługuje on używany przez wiele wystąpień `CSimpleStringT`, wskaźnik do Menedżera zabezpieczać ciągu ma zostać zwrócony.  
  
> [!NOTE]
>  Aby uzyskać przykłady użycia, zobacz [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
##  <a name="free"></a>  IAtlStringMgr::Free  
 Zwalnia struktury danych ciągu.  
  
```
void Free(CStringData* pData) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *pData*  
 Wskaźnik do bloku pamięci, który ma zostać zwolniony.  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia blok pamięci określonej uprzednio przydzielonej przez [przydziel](#allocate) lub [ponowne przydzielenie](../../atl/reference/iatlmemmgr-class.md#reallocate).  
  
> [!NOTE]
>  Aby uzyskać przykłady użycia, zobacz [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
##  <a name="getnilstring"></a>  IAtlStringMgr::GetNilString  
 Zwraca wskaźnik do struktury danych ciągu dla pustego ciągu.  
  
```
CStringData* GetNilString() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CStringData` obiekt używany do reprezentowania pusty ciąg.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę funkcję, aby zwrócić reprezentację pusty ciąg.  
  
> [!NOTE]
>  Podczas implementowania Menedżera niestandardowy ciąg, ta funkcja nigdy nie musi się niepowodzeniem. Może to zapewnić, osadzając wystąpienie `CNilStringData` w ciągu Menedżera klasy i powrót wskaźnika do tego wystąpienia.  
  
> [!NOTE]
>  Aby uzyskać przykłady użycia, zobacz [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
##  <a name="reallocate"></a>  IAtlStringMgr::Reallocate  
 Przydzieli struktury danych ciągu.  
  
```
CStringData* Reallocate(  
 CStringData* pData,
 int nAllocLength,
 int nCharSize) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *pData*  
 Wskaźnik do pamięci uprzednio przydzielonej przez tego menedżera pamięci.  
  
 *nAllocLength*  
 Liczba znaków w nowy blok pamięci.  
  
 *nCharSize*  
 Rozmiar (w bajtach) to typ znaku używany przez Menedżera ciągów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do początku bloku nowo alokacji pamięci.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę funkcję, aby zmienić rozmiar istniejącej bloku pamięci określonej przez *pData*.  
  
 Wywołaj [IAtlStringMgr::Free](#free) zwolnienie pamięci przydzielonej przez tę metodę.  
  
> [!NOTE]
>  Aby uzyskać przykłady użycia, zobacz [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy współdzielone ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)


