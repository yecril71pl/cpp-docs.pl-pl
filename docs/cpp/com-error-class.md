---
title: _com_error — Klasa
ms.date: 11/04/2016
f1_keywords:
- _com_error
helpviewer_keywords:
- _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
ms.openlocfilehash: ace3ac33e4dccd66c0a44095533d657e32b15f1c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837817"
---
# <a name="_com_error-class"></a>_com_error — Klasa

**Specyficzne dla firmy Microsoft**

Obiekt **_com_error** reprezentuje warunek wyjątku wykrywany przez funkcje otoki obsługi błędów w plikach nagłówkowych wygenerowanych z biblioteki typów lub przez jedną z klas obsługi modelu com. Klasa **_com_error** hermetyzuje kod błędu HRESULT i dowolny skojarzony `IErrorInfo Interface` obiekt.

### <a name="construction"></a>Budownictwo

| Nazwa | Opis |
|-|-|
|[_com_error](../cpp/com-error-com-error.md)|Konstruuje obiekt **_com_error** .|

### <a name="operators"></a>Operatory

| Nazwa | Opis |
|-|-|
|[operator =](../cpp/com-error-operator-equal.md)|Przypisuje istniejący obiekt **_com_error** do innego.|

### <a name="extractor-functions"></a>Funkcje wyodrębniania

| Nazwa | Opis |
|-|-|
|[Błąd](../cpp/com-error-error.md)|Pobiera wartość HRESULT przekazaną do konstruktora.|
|[ErrorInfo](../cpp/com-error-errorinfo.md)|Pobiera `IErrorInfo` obiekt przesłany do konstruktora.|
|[Kodostrzeżenia](../cpp/com-error-wcode.md)|Pobiera 16-bitowy kod błędu mapowany na hermetyzowaną wartość HRESULT.|

### <a name="ierrorinfo-functions"></a>Funkcje IErrorInfo

| Nazwa | Opis |
|-|-|
|[Opis](../cpp/com-error-description.md)|Wywołuje `IErrorInfo::GetDescription` funkcję.|
|[Atrybut HelpContext](../cpp/com-error-helpcontext.md)|Wywołuje `IErrorInfo::GetHelpContext` funkcję.|
|[HelpFile](../cpp/com-error-helpfile.md)|Calls — `IErrorInfo::GetHelpFile` Funkcja|
|[Element źródłowy](../cpp/com-error-source.md)|Wywołuje `IErrorInfo::GetSource` funkcję.|
|[IDENT](../cpp/com-error-guid.md)|Wywołuje `IErrorInfo::GetGUID` funkcję.|

### <a name="format-message-extractor"></a>Wyodrębnianie formatu komunikatów

| Nazwa | Opis |
|-|-|
|[ErrorMessage](../cpp/com-error-errormessage.md)|Pobiera komunikat ciągu dla HRESULT przechowywanego w obiekcie **_com_error** .|

### <a name="exepinfowcode-to-hresult-mappers"></a>ExepInfo. Kodostrzeżenia do mapera HRESULT

| Nazwa | Opis |
|-|-|
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|Maps 32-bit HRESULT do 16-bitowego `wCode` .|
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|Mapuje 16-bitowe `wCode` do 32-BITOWEJ HRESULT.|

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<comdef.h>

`Lib:` comsuppw. lib lub comsuppwd. lib (patrz [/Zc: wchar_t (Wchar_t jest typem natywnym)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) , aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz też

[Klasy obsługi kompilatora COM](../cpp/compiler-com-support-classes.md)<br/>
[IErrorInfo, interfejs](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)
