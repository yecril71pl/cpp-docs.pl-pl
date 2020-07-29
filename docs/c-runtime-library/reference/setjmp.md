---
title: setjmp
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
ms.openlocfilehash: beaf56a03c1bd157257d604bfd0ebefb219d0225
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226154"
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

Zwraca wartość 0 po zapisaniu środowiska stosu. Jeśli **setjmp** zwraca jako wynik `longjmp` wywołania, zwraca argument *wartości* `longjmp` , lub jeśli argument *wartości* `longjmp` jest 0, **setjmp** zwraca 1. Brak powrotu błędu.

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

## <a name="see-also"></a>Zobacz także

[Proces i kontrola środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[longjmp](longjmp.md)
