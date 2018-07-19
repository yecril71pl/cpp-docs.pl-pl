---
title: _com_error — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error
dev_langs:
- C++
helpviewer_keywords:
- _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d59782b62ddfb51601505be6d12f01ce14cd4f1
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/13/2018
ms.locfileid: "39026637"
---
# <a name="comerror-class"></a>_com_error — Klasa
**Microsoft Specific**  
  
 Element `_com_error` obiektu przedstawia warunek wyjątku, wykrywany przez funkcje otoki obsługi błędów w plikach nagłówkowych wygenerowane z biblioteki typów lub za pomocą jednej z klas obsługi COM. `_com_error` Klasa hermetyzuje kod błędu HRESULT i wszelkie powiązane `IErrorInfo Interface` obiektu.  
  
### <a name="construction"></a>Konstrukcja  
  
|||  
|-|-|  
|[_com_error](../cpp/com-error-com-error.md)|Konstruuje `_com_error` obiektu.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator =](../cpp/com-error-operator-equal.md)|Przypisuje istniejące `_com_error` obiektu do drugiego.|  
  
### <a name="extractor-functions"></a>Ekstraktor funkcji  
  
|||  
|-|-|  
|[Error](../cpp/com-error-error.md)|Pobiera wartość HRESULT przekazany do konstruktora.|  
|[ErrorInfo](../cpp/com-error-errorinfo.md)|Pobiera `IErrorInfo` obiekt przekazany do konstruktora.|  
|[WCode](../cpp/com-error-wcode.md)|Pobiera kod błędu 16-bitowych zmapowany do zhermetyzowanego HRESULT.|  
  
### <a name="ierrorinfo-functions"></a>Funkcje IErrorInfo  
  
|||  
|-|-|  
|[Opis](../cpp/com-error-description.md)|Wywołania `IErrorInfo::GetDescription` funkcji.|  
|[HelpContext](../cpp/com-error-helpcontext.md)|Wywołania `IErrorInfo::GetHelpContext` funkcji.|  
|[HelpFile —](../cpp/com-error-helpfile.md)|Wywołania `IErrorInfo::GetHelpFile` — funkcja|  
|[Źródło](../cpp/com-error-source.md)|Wywołania `IErrorInfo::GetSource` funkcji.|  
|[IDENTYFIKATOR GUID](../cpp/com-error-guid.md)|Wywołania `IErrorInfo::GetGUID` funkcji.|  
  
### <a name="format-message-extractor"></a>Format komunikatu ekstraktory  
  
|||  
|-|-|  
|[Komunikat o błędzie](../cpp/com-error-errormessage.md)|Pobiera ciąg komunikatu dla przechowywanych we właściwości HRESULT `_com_error` obiektu.|  
  
### <a name="exepinfowcode-to-hresult-mappers"></a>ExepInfo.wCode do liczby Maperów HRESULT  
  
|||  
|-|-|  
|[Hresulttowcode —](../cpp/com-error-hresulttowcode.md)|Mapuje HRESULT 32-bitowego do 16-bitowych `wCode`.|  
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|Mapuje 16-bitowych `wCode` HRESULT 32-bitowych.|  
  
**END specyficzny dla Microsoft**  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<comdef.h >  
  
 `Lib:` comsuppw.lib lub comsuppwd.lib (zobacz [/Zc: wchar_t (wchar_t jest typem natywnym)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) Aby uzyskać więcej informacji)  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator klas obsługi COM](../cpp/compiler-com-support-classes.md)   
 [Interfejs IErrorInfo](http://msdn.microsoft.com/4dda6909-2d9a-4727-ae0c-b5f90dcfa447)