---
title: "_com_error — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_error
dev_langs: C++
helpviewer_keywords: _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1cb40690770094582eee87294d250d16d22b9c0c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="comerror-class"></a>_com_error — Klasa
**Dotyczące firmy Microsoft**  
  
 A `_com_error` obiekt reprezentuje wykryte przez funkcje otoki obsługi błędów w plikach nagłówka wygenerowane z biblioteki typu lub jednej z klas obsługi COM warunku wyjątku. `_com_error` Klasa hermetyzuje `HRESULT` kod błędu i wszelkie powiązane `IErrorInfo Interface` obiektu.  
  
### <a name="construction"></a>Konstrukcji  
  
|||  
|-|-|  
|[_com_error](../cpp/com-error-com-error.md)|Konstruuje `_com_error` obiektu.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator =](../cpp/com-error-operator-equal.md)|Przypisuje istniejące `_com_error` obiektu do innego.|  
  
### <a name="extractor-functions"></a>Funkcje katalogu  
  
|||  
|-|-|  
|[Błąd](../cpp/com-error-error.md)|Pobiera `HRESULT` przekazany do konstruktora.|  
|[ErrorInfo](../cpp/com-error-errorinfo.md)|Pobiera `IErrorInfo` obiekt przekazany do konstruktora.|  
|[WCode](../cpp/com-error-wcode.md)|Pobiera kod błędu 16-bitowych przypisywane do hermetyzowany `HRESULT`.|  
  
### <a name="ierrorinfo-functions"></a>Funkcje IErrorInfo  
  
|||  
|-|-|  
|[Opis](../cpp/com-error-description.md)|Wywołania `IErrorInfo::GetDescription` funkcji.|  
|[HelpContext](../cpp/com-error-helpcontext.md)|Wywołania `IErrorInfo::GetHelpContext` funkcji.|  
|[HelpFile](../cpp/com-error-helpfile.md)|Wywołania `IErrorInfo::GetHelpFile` — funkcja|  
|[Źródło](../cpp/com-error-source.md)|Wywołania `IErrorInfo::GetSource` funkcji.|  
|[IDENTYFIKATOR GUID](../cpp/com-error-guid.md)|Wywołania `IErrorInfo::GetGUID` funkcji.|  
  
### <a name="format-message-extractor"></a>Format komunikatu wyodrębniania  
  
|||  
|-|-|  
|[Komunikat o błędzie](../cpp/com-error-errormessage.md)|Pobiera ciąg komunikatu HRESULT przechowywane w `_com_error` obiektu.|  
  
### <a name="exepinfowcode-to-hresult-mappers"></a>ExepInfo.wCode do mapowań HRESULT  
  
|||  
|-|-|  
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|Mapuje 32-bitowych `HRESULT` do 16-bitowych `wCode`.|  
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|Mapuje 16-bitowych `wCode` do 32-bitowych `HRESULT`.|  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** comdef.h  
  
 `Lib:`comsuppw.lib lub comsuppwd.lib (zobacz [/Zc: wchar_t (wchar_t jest typem natywnym)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) Aby uzyskać więcej informacji)  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator klas obsługi COM](../cpp/compiler-com-support-classes.md)   
 [Interfejs IErrorInfo](http://msdn.microsoft.com/en-us/4dda6909-2d9a-4727-ae0c-b5f90dcfa447)