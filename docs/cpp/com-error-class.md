---
title: _com_error — Klasa
ms.date: 11/04/2016
f1_keywords:
- _com_error
helpviewer_keywords:
- _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
ms.openlocfilehash: 828a1ec68fef631700d5b64e6aeeec6660acf9a8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498747"
---
# <a name="_com_error-class"></a>_com_error — Klasa

**Microsoft Specific**

Obiekt **_com_error** reprezentuje warunek wyjątku wykrywany przez funkcje otoki obsługi błędów w plikach nagłówkowych wygenerowanych z biblioteki typów lub przez jedną z klas obsługi com. Klasa **_com_error** hermetyzuje kod błędu HRESULT i dowolny skojarzony `IErrorInfo Interface` obiekt.

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
|[Error](../cpp/com-error-error.md)|Pobiera wartość HRESULT przekazaną do konstruktora.|
|[ErrorInfo](../cpp/com-error-errorinfo.md)|`IErrorInfo` Pobiera obiekt przesłany do konstruktora.|
|[WCode](../cpp/com-error-wcode.md)|Pobiera 16-bitowy kod błędu mapowany na hermetyzowaną wartość HRESULT.|

### <a name="ierrorinfo-functions"></a>Funkcje IErrorInfo

|||
|-|-|
|[Opis](../cpp/com-error-description.md)|Wywołuje `IErrorInfo::GetDescription` funkcję.|
|[HelpContext](../cpp/com-error-helpcontext.md)|Wywołuje `IErrorInfo::GetHelpContext` funkcję.|
|[HelpFile](../cpp/com-error-helpfile.md)|Calls `IErrorInfo::GetHelpFile` — funkcja|
|[Element źródłowy](../cpp/com-error-source.md)|Wywołuje `IErrorInfo::GetSource` funkcję.|
|[IDENT](../cpp/com-error-guid.md)|Wywołuje `IErrorInfo::GetGUID` funkcję.|

### <a name="format-message-extractor"></a>Wyodrębnianie formatu komunikatów

|||
|-|-|
|[ErrorMessage](../cpp/com-error-errormessage.md)|Pobiera komunikat ciągu dla HRESULT przechowywanego w obiekcie **_com_error** .|

### <a name="exepinfowcode-to-hresult-mappers"></a>ExepInfo. Kodostrzeżenia do mapera HRESULT

|||
|-|-|
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|Maps 32-bit HRESULT do 16-bitowego `wCode`.|
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|Mapuje 16- `wCode` bitowe do 32-bitowej HRESULT.|

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<comdef. h >

`Lib:`comsuppw. lib lub comsuppwd. lib (patrz [/Zc: wchar_t (Wchar_t jest typem natywnym)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) , aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz także

[Kompilator klas obsługi COM](../cpp/compiler-com-support-classes.md)<br/>
[IErrorInfo, interfejs](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)