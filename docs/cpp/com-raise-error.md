---
title: _com_raise_error
ms.date: 11/04/2016
f1_keywords:
- _com_raise_error
helpviewer_keywords:
- _com_raise_error function
ms.assetid: a98226c2-c3fe-44f1-8ff5-85863de11cd6
ms.openlocfilehash: f5efbe98a489a380c4e9be5a0e40603be2a409c0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745079"
---
# <a name="_com_raise_error"></a>_com_raise_error

**Specyficzne dla firmy Microsoft**

Rzuca [_com_error](../cpp/com-error-class.md) w odpowiedzi na błąd.

## <a name="syntax"></a>Składnia

```cpp
void __stdcall _com_raise_error(
   HRESULT hr,
   IErrorInfo* perrinfo = 0
);
```

#### <a name="parameters"></a>Parametry

*Hr*<br/>
informacje HRESULT.

*perrinfo (perrinfo)*<br/>
`IErrorInfo`Obiektu.

## <a name="remarks"></a>Uwagi

**_com_raise_error**, który jest zdefiniowany w \<comdef.h>, może być zastąpiony przez wersję napisaną przez użytkownika o tej samej nazwie i prototypie. Można to zrobić, jeśli `#import` chcesz użyć, ale nie chcesz używać obsługi wyjątków C++. W takim przypadku wersja użytkownika **_com_raise_error** może zdecydować `longjmp` się na zrobienie lub wyświetlenie okna komunikatu i zatrzymanie. Wersja użytkownika nie powinna zwracać, jednak, ponieważ kod obsługi COM kompilatora nie oczekuje, że do zwrócenia.

Można również użyć [_set_com_error_handler,](../cpp/set-com-error-handler.md) aby zastąpić domyślną funkcję obsługi błędów.

Domyślnie **_com_raise_error** jest definiowana w następujący sposób:

```cpp
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {
   throw _com_error(hr, perrinfo);
}
```

**ZAKOŃCZ Specyficzne dla firmy Microsoft**

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<comdef.h>

**Lib:** Jeśli **wchar_t jest natywna** opcja kompilatora typu macierzystego, użyj comsuppw.lib lub comsuppwd.lib. Jeśli **wchar_t jest Typem macierzystym,** użyj pliku comsupp.lib. Aby uzyskać więcej informacji, zobacz [/Zc:wchar_t (wchar_t jest typem macierzystym).](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)

## <a name="see-also"></a>Zobacz też

[Funkcje globalne kompilatora COM](../cpp/compiler-com-global-functions.md)<br/>
[_set_com_error_handler](../cpp/set-com-error-handler.md)
