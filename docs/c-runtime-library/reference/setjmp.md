---
title: setjmp
description: Dokumentacja interfejsu API dla setjmp; powoduje to zapisanie bieżącego stanu programu.
ms.date: 08/14/2018
api_name:
- setjmp
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- setjmp
helpviewer_keywords:
- programs [C++], saving states
- current state
- setjmp function
ms.assetid: 684a8b27-e8eb-455b-b4a8-733ca1cbd7d2
ms.openlocfilehash: 3ea08e5379433e313e08870f735322b7d985aa64
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555608"
---
# <a name="setjmp"></a>setjmp

Zapisuje bieżący stan programu.

## <a name="syntax"></a>Składnia

```C
int setjmp(
   jmp_buf env
);
```

### <a name="parameters"></a>Parametry

*kopert*<br/>
Zmienna, w której jest przechowywane środowisko.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0 po zapisaniu środowiska stosu. Jeśli **setjmp** zwraca jako wynik `longjmp` wywołania, zwraca argument *wartości* `longjmp` , lub jeśli argument *wartości* `longjmp` jest 0, **setjmp** zwraca 1. Nie ma żadnego powrotu błędu.

## <a name="remarks"></a>Uwagi

Funkcja **setjmp** zapisuje środowisko stosu, które można później przywrócić, używając `longjmp` . Używane razem, **setjmp** i `longjmp` umożliwiają wykonywanie nielokalnych **`goto`** . Są one zazwyczaj używane do przekazywania kontroli wykonywania do kodu obsługi błędów lub odzyskiwania w wcześniej wywołanej procedurze bez używania normalnych konwencji wywoływania lub powrotu.

Wywołanie **setjmp** zapisuje bieżące środowisko stosu w *ENV*. Kolejne wywołanie w celu `longjmp` przywrócenia zapisanego środowiska i zwraca kontrolę do punktu zaraz po odpowiednim wywołaniu **setjmp** . Wszystkie zmienne (z wyjątkiem zmiennych rejestru) dostępne dla procedury otrzymującej kontrolę zawierają wartości, które zostały `longjmp` wywołane.

Nie można użyć **setjmp** do przechodzenia z kodu natywnego do zarządzanego.

**Specyficzne dla firmy Microsoft**

W programie Microsoft C++ Code w systemie Windows **longjmp** używa tej samej semantyki odwinięcia stosu, co kod obsługi wyjątków. Można bezpiecznie użyć w tych samych miejscach, które mogą być zgłaszane wyjątki C++. Takie użycie nie jest jednak przenośne i zawiera pewne ważne zastrzeżenia. Aby uzyskać szczegółowe informacje, zobacz [longjmp](longjmp.md).

**ZAKOŃCZENIE określonych przez firmę Microsoft**

> [!NOTE]
> W kodzie Portable C++ nie można przyjąć `setjmp` ani `longjmp` obsługiwać semantyki obiektów c++. W `setjmp` / `longjmp` odniesieniu do pary wywołań występuje niezdefiniowane zachowanie, Jeśli zastępowanie `setjmp` i `longjmp` **`catch`** i **`throw`** wywoła wszystkie nieuproszczone destruktory dla wszystkich obiektów automatycznych. W programach w języku C++ zalecamy korzystanie z mechanizmu obsługi wyjątków C++.

Aby uzyskać więcej informacji, zobacz [Korzystanie z setjmp i longjmp](../../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**setjmp**|\<setjmp.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zapoznaj się z przykładem [_fpreset](fpreset.md).

## <a name="see-also"></a>Zobacz też

[Proces i kontrola środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[longjmp](longjmp.md)
