---
title: Klasa CDefaultCharTraits | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits::CharToLower
- ATLCOLL/ATL::CDefaultCharTraits::CharToUpper
dev_langs: C++
helpviewer_keywords: CDefaultCharTraits class
ms.assetid: f94a3934-597f-401d-8513-ed6924ae069a
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 02595c426a631e15bf2f1b5baed2550a8befe20a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
  
##  <a name="chartolower"></a>CDefaultCharTraits::CharToLower  
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
  
##  <a name="chartoupper"></a>CDefaultCharTraits::CharToUpper  
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
