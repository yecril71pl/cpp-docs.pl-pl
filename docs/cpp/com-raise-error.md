---
title: _com_raise_error
ms.date: 11/04/2016
f1_keywords:
- _com_raise_error
helpviewer_keywords:
- _com_raise_error function
ms.assetid: a98226c2-c3fe-44f1-8ff5-85863de11cd6
ms.openlocfilehash: 5790fceef26d6de4edff604270cc7108f764aced
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399255"
---
# <a name="comraiseerror"></a>_com_raise_error

**Microsoft Specific**

Zgłasza [_com_error](../cpp/com-error-class.md) w odpowiedzi na błąd.

## <a name="syntax"></a>Składnia

```
void __stdcall _com_raise_error(
   HRESULT hr,
   IErrorInfo* perrinfo = 0
);
```

#### <a name="parameters"></a>Parametry

*godz.*<br/>
Informacje o HRESULT.

*perrinfo*<br/>
`IErrorInfo` obiekt.

## <a name="remarks"></a>Uwagi

**_com_raise_error —**, który jest zdefiniowany w \<comdef.h >, może być zastąpiony napisany przez użytkownika wersję taką samą nazwę i prototypu. To było zrobić, jeśli chcesz używać `#import` , ale nie chcesz używać obsługę wyjątków C++. W takim przypadku użytkownik wersji **_com_raise_error —** zdecydować, czy `longjmp` lub wyświetlić okno komunikatu i zatrzymany. Wersja użytkownika nie powinny zwracać, jednak, ponieważ kod obsługi kompilatora COM nie oczekuje do zwrócenia.

Można również użyć [_set_com_error_handler —](../cpp/set-com-error-handler.md) zastąpić domyślną funkcję obsługi błędów.

Domyślnie **_com_raise_error —** jest zdefiniowana w następujący sposób:

```cpp
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {
   throw _com_error(hr, perrinfo);
}
```

**END specyficzny dla Microsoft**

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<comdef.h >

**Biblioteki:** Jeśli **wchar_t jest typem natywnym** — opcja kompilatora jest włączona, użyj comsuppw.lib lub comsuppwd.lib. Jeśli **wchar_t jest typem natywnym** jest wyłączone, użyj comsupp.lib. Aby uzyskać więcej informacji, zobacz [/Zc: wchar_t (wchar_t jest typem natywnym)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

## <a name="see-also"></a>Zobacz także

[Funkcje globalne kompilatora COM](../cpp/compiler-com-global-functions.md)<br/>
[_set_com_error_handler](../cpp/set-com-error-handler.md)