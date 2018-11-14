---
title: _com_error — Klasa
ms.date: 11/04/2016
f1_keywords:
- _com_error
helpviewer_keywords:
- _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
ms.openlocfilehash: 8ed1521cbf768e5b473281e5f9b7c6597cdc4692
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519558"
---
# <a name="comerror-class"></a>_com_error — Klasa

**Microsoft Specific**

A **_com_error** obiektu przedstawia warunek wyjątku, wykrywany przez funkcje otoki obsługi błędów w plikach nagłówkowych wygenerowane z biblioteki typów lub za pomocą jednej z klas obsługi COM. **_Com_error** klasa hermetyzuje kod błędu HRESULT i wszelkie powiązane `IErrorInfo Interface` obiektu.

### <a name="construction"></a>Konstrukcja

|||
|-|-|
|[_com_error](../cpp/com-error-com-error.md)|Konstruuje **_com_error** obiektu.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator =](../cpp/com-error-operator-equal.md)|Przypisuje istniejące **_com_error** obiektu do drugiego.|

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
|[Komunikat o błędzie](../cpp/com-error-errormessage.md)|Pobiera ciąg komunikatu dla przechowywanych we właściwości HRESULT **_com_error** obiektu.|

### <a name="exepinfowcode-to-hresult-mappers"></a>ExepInfo.wCode do liczby Maperów HRESULT

|||
|-|-|
|[Hresulttowcode —](../cpp/com-error-hresulttowcode.md)|Mapuje HRESULT 32-bitowego do 16-bitowych `wCode`.|
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|Mapuje 16-bitowych `wCode` HRESULT 32-bitowych.|

**END specyficzny dla Microsoft**

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<comdef.h >

`Lib:` comsuppw.lib lub comsuppwd.lib (zobacz [/Zc: wchar_t (wchar_t jest typem natywnym)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) Aby uzyskać więcej informacji)

## <a name="see-also"></a>Zobacz także

[Kompilator klas obsługi COM](../cpp/compiler-com-support-classes.md)<br/>
[Interfejs IErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo)