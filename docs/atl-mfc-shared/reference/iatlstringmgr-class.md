---
title: Klasa IAtlStringMgr | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 85b99b0b1f35ecbc35b4096ac8c2260d0a55680d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="iatlstringmgr-class"></a>Klasa IAtlStringMgr
Ta klasa reprezentuje interfejs służący do `CStringT` Menedżer pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```
__interface IAtlStringMgr
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Przydziel](#allocate)|Wywołanie tej metody można przydzielić nowej struktury danych ciągu.|  
|[Klonowania](#clone)|Wywołanie tej metody do zwraca wskaźnik do nowego Menedżera ciąg do użycia z innego wystąpienia `CSimpleStringT`.|  
|[W warstwie bezpłatna](#free)|Wywołać tę metodę można zwolnić struktury danych ciągu.|  
|[GetNilString](#getnilstring)|Zwraca wskaźnik do `CStringData` obiekt używany przez obiekty pusty ciąg.|  
|[Ponowne przydzielenie](#reallocate)|Wywołaj tę metodę, aby ponownie przydzielić to struktura danych ciągu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs zarządzania pamięcią, używane przez MFC niezależne od klasy ciągu; takie jak [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), [CStringT](../../atl-mfc-shared/reference/cstringt-class.md), i [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md).  
  
 Ta klasa umożliwia również implementować Menedżer pamięci niestandardowych dla klasy niestandardowy ciąg. Aby uzyskać więcej informacji, zobacz [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsimpstr.h  
  
##  <a name="allocate"></a>IAtlStringMgr::Allocate  
 Przydziela strukturą danych ciągu.  
  
```
CStringData* Allocate(int nAllocLength,int nCharSize) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nAllocLength`  
 Liczba znaków w nowego bloku pamięci.  
  
 `nCharSize`  
 Rozmiar (w bajtach) używaną przez Menedżera ciąg typu znaków.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do bloku nowo alokacji pamięci.  
  
> [!NOTE]
>  Nie można sygnalizować błąd alokacji przez Zgłaszanie wyjątku. Zamiast tego błąd alokacji powinien zostać zgłoszony przez zwrócenie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie [IAtlStringMgr::Free](#free) lub [IAtlStringMgr::ReAllocate](#reallocate) zwolnienia pamięci przydzielonej przez tę metodę.  
  
> [!NOTE]
>  Przykłady użycia można znaleźć [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
##  <a name="clone"></a>IAtlStringMgr::Clone  
 Zwraca wskaźnik do nowego Menedżera ciąg do użycia z innego wystąpienia `CSimpleStringT`.  
  
```
IAtlStringMgr* Clone() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca kopię `IAtlStringMgr` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Najczęściej wywoływane przez platformę, gdy Menedżer ciągów jest wymagany dla nowych parametrów. W większości przypadków **to** zwracany jest wskaźnik.  
  
 Jednak jeśli Menedżer pamięci nie obsługuje on używany przez wiele wystąpień `CSimpleStringT`, wskaźnik do Menedżera zabezpieczać ciąg ma zostać zwrócony.  
  
> [!NOTE]
>  Przykłady użycia można znaleźć [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
##  <a name="free"></a>IAtlStringMgr::Free  
 Zwalnia to struktura danych ciągu.  
  
```
void Free(CStringData* pData) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pData`  
 Wskaźnik do bloku pamięci, który ma zostać zwolniony.  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia blok pamięci określony wcześniej przydzielone przez [przydziel](#allocate) lub [ponowne przydzielenie](../../atl/reference/iatlmemmgr-class.md#reallocate).  
  
> [!NOTE]
>  Przykłady użycia można znaleźć [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
##  <a name="getnilstring"></a>IAtlStringMgr::GetNilString  
 Zwraca wskaźnik do struktury danych ciąg dla pustego ciągu.  
  
```
CStringData* GetNilString() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CStringData` obiekt używany do reprezentowania ciągiem pustym.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji do zwrócenia reprezentację ciągiem pustym.  
  
> [!NOTE]
>  Podczas implementowania Menedżera niestandardowy ciąg, ta funkcja musi nigdy nie zakończyć się niepowodzeniem. Można to zapewnić osadzanie wystąpienia **CNilStringData** w ciągu Menedżera klasy i powrotu wskaźnik do tego wystąpienia.  
  
> [!NOTE]
>  Przykłady użycia można znaleźć [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
##  <a name="reallocate"></a>IAtlStringMgr::Reallocate  
 Przydziela ponownie to struktura danych ciągu.  
  
```
CStringData* Reallocate(  
 CStringData* pData,
 int nAllocLength,
 int nCharSize) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pData`  
 Wskaźnik do pamięci przydzielona wcześniej przez tego menedżera pamięci.  
  
 `nAllocLength`  
 Liczba znaków w nowego bloku pamięci.  
  
 `nCharSize`  
 Rozmiar (w bajtach) używaną przez Menedżera ciąg typu znaków.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do rozpoczęcia bloku nowo alokacji pamięci.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, aby zmienić rozmiar istniejącego bloku pamięci określony przez `pData`.  
  
 Wywołanie [IAtlStringMgr::Free](#free) zwolnienia pamięci przydzielonej przez tę metodę.  
  
> [!NOTE]
>  Przykłady użycia można znaleźć [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [ATL/MFC udostępnionych klas](../../atl-mfc-shared/atl-mfc-shared-classes.md)


