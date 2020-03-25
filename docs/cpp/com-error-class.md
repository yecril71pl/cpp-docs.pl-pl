---
title: _com_error — Klasa
ms.date: 11/04/2016
f1_keywords:
- _com_error
helpviewer_keywords:
- _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
ms.openlocfilehash: 0c33791fbe6011a3eddc6e535a3a4ed838e5e06c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180813"
---
# <a name="_com_error-class"></a>_com_error — Klasa

**Specyficzne dla firmy Microsoft**

Obiekt **_com_error** reprezentuje warunek wyjątku wykrywany przez funkcje otoki obsługi błędów w plikach nagłówkowych wygenerowanych z biblioteki typów lub przez jedną z klas obsługi modelu com. Klasa **_com_error** hermetyzuje kod błędu HRESULT i wszystkie powiązane `IErrorInfo Interface` obiektu.

### <a name="construction"></a>Zrekonstruowan

|||
|-|-|
|[_com_error](../cpp/com-error-com-error.md)|Konstruuje obiekt **_com_error** .|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator =](../cpp/com-error-operator-equal.md)|Przypisuje istniejący obiekt **_com_error** do innego.|

### <a name="extractor-functions"></a>Funkcje wyodrębniania

|||
|-|-|
|[Błąd](../cpp/com-error-error.md)|Pobiera wartość HRESULT przekazaną do konstruktora.|
|[ErrorInfo](../cpp/com-error-errorinfo.md)|Pobiera obiekt `IErrorInfo` przekazywać do konstruktora.|
|[Kodostrzeżenia](../cpp/com-error-wcode.md)|Pobiera 16-bitowy kod błędu mapowany na hermetyzowaną wartość HRESULT.|

### <a name="ierrorinfo-functions"></a>Funkcje IErrorInfo

|||
|-|-|
|[Opis](../cpp/com-error-description.md)|Wywołuje funkcję `IErrorInfo::GetDescription`.|
|[Atrybut HelpContext](../cpp/com-error-helpcontext.md)|Wywołuje funkcję `IErrorInfo::GetHelpContext`.|
|[HelpFile](../cpp/com-error-helpfile.md)|Wywołuje funkcję `IErrorInfo::GetHelpFile`|
|[Element źródłowy](../cpp/com-error-source.md)|Wywołuje funkcję `IErrorInfo::GetSource`.|
|[IDENT](../cpp/com-error-guid.md)|Wywołuje funkcję `IErrorInfo::GetGUID`.|

### <a name="format-message-extractor"></a>Wyodrębnianie formatu komunikatów

|||
|-|-|
|[ErrorMessage](../cpp/com-error-errormessage.md)|Pobiera komunikat ciągu dla HRESULT przechowywanego w obiekcie **_com_error** .|

### <a name="exepinfowcode-to-hresult-mappers"></a>ExepInfo. Kodostrzeżenia do mapera HRESULT

|||
|-|-|
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|Odwzorowuje 32-bitowy wynik HRESULT na 16-bitowy `wCode`.|
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|Mapuje 16-bitowe `wCode` na 32-bitową wartość HRESULT.|

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<comdef. h >

`Lib:` comsuppw. lib lub comsuppwd. lib (patrz [/Zc: wchar_t (Wchar_t jest typem natywnym)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) , aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz też

[Kompilator klas obsługi COM](../cpp/compiler-com-support-classes.md)<br/>
[IErrorInfo, interfejs](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)
