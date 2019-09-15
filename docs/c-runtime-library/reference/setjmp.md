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
ms.openlocfilehash: 4a88467f5b94ceae4281a35f1486380a877be2e5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948244"
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

Zwraca wartość 0 po zapisaniu środowiska stosu. Jeśli **setjmp** `longjmp` zwraca jako wynik wywołania, zwraca `longjmp` argument `longjmp` *wartości* , lub jeśli argument *wartości* jest 0, **setjmp** zwraca 1. Brak powrotu błędu.

## <a name="remarks"></a>Uwagi

Funkcja **setjmp** zapisuje środowisko stosu, które można później przywrócić, używając `longjmp`. Gdy są używane razem , setjmp `longjmp` i zapewniają sposób wykonywania nielokalnego elementu **goto**. Są one zazwyczaj używane do przekazywania kontroli wykonywania do kodu obsługi błędów lub odzyskiwania w wcześniej wywołanej procedurze bez używania normalnych konwencji wywoływania lub powrotu.

Wywołanie **setjmp** zapisuje bieżące środowisko stosu w *ENV*. Kolejne wywołanie w celu `longjmp` przywrócenia zapisanego środowiska i zwraca kontrolę do punktu zaraz po odpowiednim wywołaniu **setjmp** . Wszystkie zmienne (z wyjątkiem zmiennych rejestru) dostępne dla procedury otrzymującej kontrolę zawierają wartości, które `longjmp` zostały wywołane.

Nie można użyć **setjmp** do przechodzenia z kodu natywnego do zarządzanego.

**Microsoft Specific**

W programie C++ Microsoft Code w systemie Windows **longjmp** używa tej samej semantyki odwracania stosu, co kod obsługi wyjątków. Można bezpiecznie użyć w tych samych miejscach, w których C++ mogą zostać zgłoszone wyjątki. Takie użycie nie jest jednak przenośne i zawiera pewne ważne zastrzeżenia. Aby uzyskać szczegółowe informacje, zobacz [longjmp](longjmp.md).

**ZAKOŃCZENIE określonych przez firmę Microsoft**

> [!NOTE]
> W kodzie C++ przenośnym nie można przyjąć `setjmp` ani `longjmp` obsługiwać C++ semantyki obiektów. `longjmp` `setjmp` W odniesieniu do pary wywołańwystępujeniezdefiniowanezachowanie,jeślizastąpienieobiektuiprzechwycenieithrowwywoławszystkienieuproszczonedestruktorydlawszystkichobiektówautomatycznych.`longjmp` `setjmp` / W C++ obszarze programy zalecamy korzystanie z C++ mechanizmu obsługi wyjątków.

Aby uzyskać więcej informacji, zobacz [Korzystanie z setjmp i longjmp](../../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**setjmp**|\<setjmp.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład dla [_fpreset](fpreset.md).

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[longjmp](longjmp.md)
