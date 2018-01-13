---
title: Klasa CStringData | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStringData
- ATLSIMPSTR/ATL::CStringData
- ATLSIMPSTR/ATL::AddRef
- ATLSIMPSTR/ATL::data
- ATLSIMPSTR/ATL::IsLocked
- ATLSIMPSTR/ATL::IsShared
- ATLSIMPSTR/ATL::Lock
- ATLSIMPSTR/ATL::Release
- ATLSIMPSTR/ATL::Unlock
- ATLSIMPSTR/ATL::nAllocLength
- ATLSIMPSTR/ATL::nDataLength
- ATLSIMPSTR/ATL::nRefs
- ATLSIMPSTR/ATL::pStringMgr
dev_langs: C++
helpviewer_keywords:
- CStringData class
- shared classes, CStringData
ms.assetid: 4e31b5ca-3dbe-4fd5-b692-8211fbfb2593
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7523ca52c0ded8ec9b3cf02dd6798beca8be5cf8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cstringdata-class"></a>Klasa CStringData
Ta klasa reprezentuje dane z obiektem ciągu.  
  
## <a name="syntax"></a>Składnia  
  
```
struct CStringData
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[AddRef](#addref)|Zwiększa liczbę odwołanie do obiektu danych ciągu.|  
|[dane](#data)|Pobiera dane znaków z obiektem ciągu.|  
|[IsLocked](#islocked)|Określa, czy jest on zablokowany buforu z obiektem ciągu skojarzone.|  
|[IsShared](#isshared)|Określa, czy buforu z obiektem ciągu skojarzona jest aktualnie udostępniony.|  
|[Blokady](#lock)|Blokuje buforu z obiektem ciągu skojarzone.|  
|[Wersja](#release)|Zwalnia obiektu określonego ciągu.|  
|[Odblokowywanie](#unlock)|Umożliwia odblokowanie buforu z obiektem ciągu skojarzone.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|[nAllocLength](#nalloclength)|Długość danych przydzielone w `XCHAR`s (bez przerywania null)|  
|[nDataLength](#ndatalength)|Długość danych aktualnie używanego w `XCHAR`s (bez przerywania null)|  
|[nRefs](#nrefs)|Bieżąca liczba odwołanie do obiektu.|  
|[pStringMgr](#pstringmgr)|Wskaźnik do Menedżera ciągu tego obiektu na ciąg.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa powinna być używana tylko przez deweloperom wdrażanie menedżerów niestandardowy ciąg. Aby uzyskać więcej informacji na menedżerów niestandardowy ciąg, zobacz [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)  
  
 Ta klasa hermetyzuje różnych typów informacji i danych skojarzonych z obiektem nowszej ciąg, takich jak [CStringT](../../atl-mfc-shared/reference/cstringt-class.md), [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), lub [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md) obiekty. Każdy obiekt nowszej ciąg zawiera wskaźnik do jego skojarzony `CStringData` obiektu, dzięki czemu wiele obiektów ciąg wskazywały ten sam obiekt danych ciągu. Ta relacja jest reprezentowana przez liczbę odwołań ( `nRefs`) z `CStringData` obiektu.  
  
> [!NOTE]
>  W niektórych przypadkach typu ciąg (takich jak **CFixedString**) nie będą współużytkować obiekt ciągu danych z więcej niż jeden obiekt nowszej ciąg. Aby uzyskać więcej informacji o tym, zobacz [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
 Te dane składa się z:  
  
-   Menedżer pamięci (typu [IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)) ciągu.  
  
-   Bieżąca długość ( [nDataLength](#ndatalength)) ciągu.  
  
-   Długość przydzielone ( [nAllocLength](#nalloclength)) ciągu. Ze względu na wydajność to może się różnić od bieżącej długości ciągu  
  
-   Bieżąca liczba odwołań ( [nRefs](#nrefs)) z `CStringData` obiektu. Ta wartość jest używana w określeniu, jak wiele obiektów typu string są takie same udostępnianie `CStringData` obiektu.  
  
-   Znak, który faktycznie buforu ( [danych](#data)) ciągu.  
  
    > [!NOTE]
    >  Bufor znak, który faktycznie z obiektem ciągu jest przydzielany przez Menedżera ciągu i jest dołączany do `CStringData` obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsimpstr.h  
  
##  <a name="addref"></a>CStringData::AddRef  
 Zwiększa liczbę odwołanie z obiektem ciągu.  
  
```
void AddRef() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwiększa liczbę odwołanie z obiektem ciągu.  
  
> [!NOTE]
>  Nie wywołuj tej metody w ciągu z liczbą ujemną odwołanie ponieważ ujemna liczebność wskazuje, że buforu ciągu jest zablokowany.  
  
##  <a name="data"></a>CStringData::data  
 Zwraca wskaźnik do buforu znak z obiektem ciągu.  
  
```
void* data() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do buforu znak z obiektem ciągu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, aby powrócić do bieżącego buforu znaku w ciągu skojarzonego obiektu.  
  
> [!NOTE]
>  Ten bufor nie jest przydzielony przez `CStringData` obiektu, ale przez Menedżera ciągu w razie potrzeby. Przydzielone, bufor jest dołączany do obiektu danych ciągu.  
  
##  <a name="islocked"></a>CStringData::IsLocked  
 Określa, czy bufor znak jest zablokowany.  
  
```
bool IsLocked() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli bufor jest zablokowany; w przeciwnym razie **false**.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji w celu ustalenia, jeśli bufor znaków ciągu obiektu jest zablokowany.  
  
##  <a name="isshared"></a>CStringData::IsShared  
 Określa, jeśli bufor znak jest udostępniony.  
  
```
bool IsShared() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli bufor jest udostępniony; w przeciwnym razie **false**.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, aby ustalić, jeśli bufor znaków ciągu obiektu danych obecnie współużytkowany wiele obiektów typu string.  
  
##  <a name="lock"></a>CStringData::Lock  
 Blokuje buforu znaków ciągu skojarzonego obiektu.  
  
```
void Lock() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji do blokowania bufora znaków ciągu obiektu danych. Blokowanie i odblokowywanie jest używany, gdy wymagany jest bezpośredni dostęp do buforu znak przez dewelopera. Dobrym przykładem blokowania dowodzą [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) i [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) metody `CSimpleStringT`.  
  
> [!NOTE]
>  Bufor znak może być zablokowany, jeśli bufor nie jest udostępniana między nowszej ciąg obiektów.  
  
##  <a name="nalloclength"></a>CStringData::nAllocLength  
 Długość buforu przydzielone znaków.  
  
```
int nAllocLength;
```  
  
### <a name="remarks"></a>Uwagi  
 Przechowuje długość buforu danych przydzielone w `XCHAR`s (bez przerywania null).  
  
##  <a name="ndatalength"></a>CStringData::nDataLength  
 Bieżąca długość z obiektem ciągu.  
  
```
int nDataLength;
```  
  
### <a name="remarks"></a>Uwagi  
 Przechowuje długość danych aktualnie używanego w `XCHAR`s (bez przerywania null).  
  
##  <a name="nrefs"></a>CStringData::nRefs  
 Liczba odwołań do obiektów danych ciągu.  
  
```
long nRefs;
```  
  
### <a name="remarks"></a>Uwagi  
 Przechowuje liczebności referencyjnej obiektu danych ciągu. Ten licznik wskazuje liczbę wyższej obiektów string skojarzonych z obiektem danych ciągu. Ujemna wartość oznacza obiekt danych ciągu jest obecnie zablokowany.  
  
##  <a name="pstringmgr"></a>CStringData::pStringMgr  
 Menedżer pamięci obiektu skojarzone parametry.  
  
```
IAtlStringMgr* pStringMgr;
```  
  
### <a name="remarks"></a>Uwagi  
 Przechowuje Menedżer pamięci dla obiektu skojarzone parametry. Aby uzyskać więcej informacji na menedżerów zarządzania pamięcią i ciągów, zobacz [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
##  <a name="release"></a>CStringData::Release  
 Zmniejsza odwołanie liczba obiektu danych ciągu.  
  
```
void Release() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, aby zmniejszyć liczbę odwołań zwalnianie `CStringData` struktury, jeśli liczba odwołań trafienia zero. Często jest to zrobić, gdy obiekt ciągu zostanie usunięta, a więc nie musi już odwołuje się do obiektu danych ciągu.  
  
 Na przykład następujący kod spowodowałoby wywołanie `CStringData::Release` dla obiekt ciągu danych skojarzonych z `str1`:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#104](../../atl-mfc-shared/codesnippet/cpp/cstringdata-class_1.cpp)]  
  
##  <a name="unlock"></a>CStringData::Unlock  
 Umożliwia odblokowanie buforu znaków ciągu skojarzonego obiektu.  
  
```
void Unlock() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, aby odblokować buforu znaków ciągu obiektu danych. Po odblokowaniu bufor jest możliwe do udostępnienia i może odwołanie do zliczenia.  
  
> [!NOTE]
>  Każde wywołanie `Lock` musi pasować do odpowiedniego wywołania `Unlock`.  
  
 Blokowanie i odblokowywanie jest używany, gdy deweloper musi zapewnić, że dane ciągu nie można udostępnić. Dobrym przykładem blokowania dowodzą [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) i [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) metody `CSimpleStringT`.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [ATL/MFC udostępnionych klas](../../atl-mfc-shared/atl-mfc-shared-classes.md)


