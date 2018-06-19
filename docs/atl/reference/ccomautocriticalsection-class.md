---
title: Klasa CComAutoCriticalSection | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection::CComAutoCriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CComAutoCriticalSection class
ms.assetid: 491a9d90-3398-4f90-88f5-fd2172a46b30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ae0c3cd1d00ce83a4e952d60a978663bfa76f814
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357232"
---
# <a name="ccomautocriticalsection-class"></a>Klasa CComAutoCriticalSection
`CComAutoCriticalSection` udostępnia metody uzyskiwania i zwalniania prawo własności obiektu sekcja krytyczna.  
  
## <a name="syntax"></a>Składnia  
  
```
class CComAutoCriticalSection : public CComCriticalSection
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComAutoCriticalSection::CComAutoCriticalSection](#ccomautocriticalsection)|Konstruktor.|  
|[CComAutoCriticalSection:: ~ CComAutoCriticalSection](#dtor)|Destruktor.|  
  
## <a name="remarks"></a>Uwagi  
 `CComAutoCriticalSection` jest podobny do klasy [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md), z wyjątkiem `CComAutoCriticalSection` automatycznie inicjuje obiekt sekcja krytyczna w konstruktorze.  
  
 Zazwyczaj `CComAutoCriticalSection` za pośrednictwem `typedef` nazwa [AutoCriticalSection](ccommultithreadmodel-class.md#autocriticalsection). Ta nazwa odwołuje się do `CComAutoCriticalSection` podczas [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) jest używany.  

  
 `Init` i `Term` metody [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) nie są dostępne w przypadku korzystania z tej klasy.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 `CComAutoCriticalSection`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcore.h  
  
##  <a name="ccomautocriticalsection"></a>  CComAutoCriticalSection::CComAutoCriticalSection  
 Konstruktor.  
  
```
CComAutoCriticalSection();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołania funkcji Win32 [InitializeCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms683472), które inicjuje obiekt sekcja krytyczna.  
  
##  <a name="dtor"></a>  CComAutoCriticalSection:: ~ CComAutoCriticalSection  
 Destruktor.  
  
```
~CComAutoCriticalSection() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołania destruktora [DeleteCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682552), który zwalnia wszystkie zasoby systemowe, używane przez obiekt sekcja krytyczna.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Klasa CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)
