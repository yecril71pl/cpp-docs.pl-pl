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
ms.openlocfilehash: ec16faa9881fc1c69dca5f8f39b8797cf0fcff0d
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947854"
---
# <a name="comerrorcomerror"></a>_com_error::_com_error
**Microsoft Specific**  
  
 Konstruuje `_com_error` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
_com_error(  
   HRESULT hr,  
   IErrorInfo* perrinfo = NULL,  
   bool fAddRef=false) throw( );  

_com_error( const _com_error& that ) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 *godz.*  
 Informacje o HRESULT.  
  
 *perrinfo*  
 `IErrorInfo` obiekt.  
  
 `bool fAddRef=false`  
 Powoduje, że Konstruktor może wywołać inną niż null AddRef `IErrorInfo` interfejsu. Zapewnia to poprawne zliczanie w przypadku typowych, której własność interfejsu jest przekazywana do `_com_error` obiektów, takich jak:  
  
```cpp 
throw _com_error(hr, perrinfo);  
```  
  
 Jeśli nie chcesz swój kod, aby przenieść własność na `_com_error` obiektu i `AddRef` jest wymagany, o które zostanie przesunięte `Release` w `_com_error` destruktora, konstruowania obiektu w następujący sposób:  
  
```cpp 
_com_error err(hr, perrinfo, true);  
```  
  
 *który*  
 Istniejące `_com_error` obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy Konstruktor tworzy nowy obiekt, biorąc pod uwagę na HRESULT i opcjonalnie `IErrorInfo` obiektu. Drugi tworzy kopię istniejącego `_com_error` obiektu.  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_error, klasa](../cpp/com-error-class.md)