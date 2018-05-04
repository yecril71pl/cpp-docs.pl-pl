---
title: _com_error::_com_error | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::_com_error
dev_langs:
- C++
helpviewer_keywords:
- _com_error method [C++]
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7d26239f6edf98e90f9d4d773d654025da410a97
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="comerrorcomerror"></a>_com_error::_com_error
**Microsoft Specific**  
  
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
 `HRESULT` Informacje.  
  
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