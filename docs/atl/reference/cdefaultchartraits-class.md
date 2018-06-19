---
title: Klasa CDefaultCharTraits | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits::CharToLower
- ATLCOLL/ATL::CDefaultCharTraits::CharToUpper
dev_langs:
- C++
helpviewer_keywords:
- CDefaultCharTraits class
ms.assetid: f94a3934-597f-401d-8513-ed6924ae069a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 24aa01ec29f063c1fa65ebe24c707deb1ea58556
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361730"
---
# <a name="cdefaultchartraits-class"></a>Klasa CDefaultCharTraits
Ta klasa zawiera dwie funkcje statyczne konwersję znaków między wielkie i małe litery.  
  
## <a name="syntax"></a>Składnia  
  
```
template <typename T>  
class CDefaultCharTraits
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ danych ma być przechowywany w kolekcji.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDefaultCharTraits::CharToLower](#chartolower)|(Statyczny) Wywołanie tej funkcji, aby przekonwertować znak na wielkie litery.|  
|[CDefaultCharTraits::CharToUpper](#chartoupper)|(Statyczny) Wywołanie tej funkcji, aby przekonwertować znak na małe litery.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa udostępnia funkcje, które są używane przez klasę [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcoll.h  
  
##  <a name="chartolower"></a>  CDefaultCharTraits::CharToLower  
 Wywołanie tej funkcji, aby przekonwertować znak na małe litery.  
  
```
static wchar_t CharToLower(wchar_t x);  
static char CharToLower(char x);
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Znak do przekonwertowania na małe litery.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#132](../../atl/codesnippet/cpp/cdefaultchartraits-class_1.cpp)]  
  
##  <a name="chartoupper"></a>  CDefaultCharTraits::CharToUpper  
 Wywołanie tej funkcji, aby przekonwertować znak na wielkie litery.  
  
```
static wchar_t CharToUpper(wchar_t x);  
static char CharToUpper(char x);
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Znak do przekonwertowania na wielkie litery.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
