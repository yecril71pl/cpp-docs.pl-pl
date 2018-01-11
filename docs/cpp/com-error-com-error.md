---
title: _com_error::_com_error | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_error::_com_error
dev_langs: C++
helpviewer_keywords: _com_error method [C++]
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: df04357afd35b546fb43c90a102b7dc0cacdc95e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="comerrorcomerror"></a>_com_error::_com_error
**Dotyczące firmy Microsoft**  
  
 Konstruuje `_com_error` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      _com_error(  
   HRESULT hr,  
   IErrorInfo* perrinfo = NULL,  
   bool fAddRef=false  
) throw( );  
_com_error(  
   const _com_error& that   
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `hr`  
 `HRESULT`informacje.  
  
 `perrinfo`  
 **IErrorInfo** obiektu.  
  
 **wartość logiczna fAddRef = false**  
 Konstruktor do wywołania AddRef na inną niż null powoduje, że **IErrorInfo** interfejsu. Zapewnia to poprawne zliczanie w typowych przypadkach, gdy przekazany własność interfejsu `_com_error` obiektów, takich jak:  
  
```  
throw _com_error(hr, perrinfo);  
```  
  
 Jeśli nie chcesz swój kod, aby przetransferować własność do `_com_error` obiektu i `AddRef` jest wymagany do przesunięcia **wersji** w `_com_error` destruktor, konstruowania obiektu w następujący sposób:  
  
```  
_com_error err(hr, perrinfo, true);  
```  
  
 `that`  
 Istniejące `_com_error` obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy konstruktora tworzy nowy obiekt podane `HRESULT` i opcjonalne **IErrorInfo** obiektu. Drugi tworzy kopię istniejącego `_com_error` obiektu.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_error, klasa](../cpp/com-error-class.md)