---
title: longjmp | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- longjmp
apilocation:
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
apitype: DLLExport
f1_keywords:
- longjmp
dev_langs:
- C++
helpviewer_keywords:
- restoring stack environment and execution locale
- longjmp function
ms.assetid: 0e13670a-5130-45c1-ad69-6862505b7a2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6c26cae9a3fe83012387c93e31c4005d5614d97
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="longjmp"></a>longjmp

Przywraca stosu środowiska i ustawień regionalnych wykonywania.

## <a name="syntax"></a>Składnia

```C
void longjmp(
   jmp_buf env,
   int value
);
```

### <a name="parameters"></a>Parametry

*ENV* zmiennej w środowisku, które są przechowywane.

*wartość* wartość zwracaną do **setjmp** wywołania.

## <a name="remarks"></a>Uwagi

**Longjmp** funkcja przywraca stosu środowiska i ustawień regionalnych wykonywania wcześniej zapisanych w *env* przez **setjmp**. **setjmp** i **longjmp** umożliwiają wykonanie nielokalne **goto**; zwykle służą one do przekazania do obsługi błędów lub odzyskiwania kodu w wcześniej wywołana procedura bez Kontrola wykonywania przy użyciu normalnych wywołanie i zwrócić konwencje.

Wywołanie **setjmp** powoduje, że do zapisania w bieżącym środowisku stosu *env*. Kolejne wywołania **longjmp** przywraca zapisanego środowiska i zwraca sterowania do punktu bezpośrednio po odpowiadającego **setjmp** wywołania. Wznawia wykonywanie tak, jakby *wartość* miał właśnie zostały zwrócone przez **setjmp** wywołania. Wartości zmiennych wszystkie (z wyjątkiem zmienne rejestru), które są dostępne dla procedury odbieranie kontroli zawierają wartości podczas obliczania miało **longjmp** została wywołana. Wartości zmiennych rejestru są nieprzewidywalne. Wartość zwrócona przez **setjmp** musi być różna od zera. Jeśli *wartość* jest przekazywany jako 0, wartość 1 zastępuje rzeczywiste powrotu.

Wywołanie **longjmp** przed funkcją, która wywołuje **setjmp** zwraca; w przeciwnym razie są nieprzewidywalne wyniki.

Sprawdź następujące ograniczenia, używając **longjmp**:

- Zakłada się, że wartości zmiennych rejestru jest taka sama. Wartości zmiennych rejestru w wywołaniu procedury **setjmp** nie mogą być przywracane do odpowiednich wartości po **longjmp** jest wykonywana.

- Nie używaj **longjmp** do przekazywania kontroli procedury obsługi przerwań, chyba że przerwania jest spowodowany przez zmiennoprzecinkowych wyjątków. W takim przypadku program może zwrócić z obsługi przerwań za pośrednictwem **longjmp** jeśli ją najpierw ponownie inicjuje pakietu zmiennoprzecinkowej matematyczny wywołując **_fpreset —**.

     **Uwaga** należy zachować ostrożność przy użyciu **setjmp** i **longjmp** w programach języka C++. Ponieważ te funkcje nie obsługują semantyki obiektu języka C++, bezpieczniej jest używany mechanizm obsługi wyjątków C++.

Aby uzyskać więcej informacji, zobacz [przy użyciu setjmp i longjmp](../../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**longjmp**|\<setjmp.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

Zobacz przykład [_fpreset —](fpreset.md).

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[setjmp](setjmp.md)<br/>
