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
ms.openlocfilehash: c1389635c3ef026e8b3a7dfe13976cca58a15a82
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406721"
---
# <a name="comerrorcomerror"></a>_com_error::_com_error
**Microsoft Specific**  
  
 Konstruuje **_com_error** obiektu.  
  
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
 Powoduje, że Konstruktor może wywołać inną niż null AddRef `IErrorInfo` interfejsu. Zapewnia to poprawne zliczanie w przypadku typowych, której własność interfejsu jest przekazywana do **_com_error** obiektów, takich jak:  
  
```cpp 
throw _com_error(hr, perrinfo);  
```  
  
 Jeśli nie chcesz swój kod, aby przenieść własność na **_com_error** obiektu i `AddRef` jest wymagany, o które zostanie przesunięte `Release` w **_com_error** destruktora, konstruowania obiektu jako następujące:  
  
```cpp 
_com_error err(hr, perrinfo, true);  
```  
  
 *który*  
 Istniejące **_com_error** obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy Konstruktor tworzy nowy obiekt, biorąc pod uwagę na HRESULT i opcjonalnie `IErrorInfo` obiektu. Drugi tworzy kopię istniejącego **_com_error** obiektu.  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz także  
 [_com_error, klasa](../cpp/com-error-class.md)