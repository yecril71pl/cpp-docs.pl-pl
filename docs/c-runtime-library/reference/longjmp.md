---
title: longjmp | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/14/2018
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
ms.openlocfilehash: 857fae2e9c38dfe2c5cd468c6d1b50c6fdd2f317
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2018
ms.locfileid: "42465994"
---
# <a name="longjmp"></a>longjmp

Przywraca stos środowiska i ustawień regionalnych wykonywania ustawiony przez `setjmp` wywołania.

## <a name="syntax"></a>Składnia

```C
void longjmp(
   jmp_buf env,
   int value
);
```

### <a name="parameters"></a>Parametry

*środowisko*  
Zmienna, w którym znajduje się środowisko.

*value*  
Wartość do zwrócenia do `setjmp` wywołania.

## <a name="remarks"></a>Uwagi

**Longjmp** funkcja przywraca stos środowiska i ustawień regionalnych wykonywania wcześniej zapisanych w *env* przez `setjmp`. `setjmp` i **longjmp** zapewniają sposób wykonania nielokalne **goto**; zazwyczaj są one używane do przekazywania formantów wykonywania do kodu obsługi błędów lub odzyskiwania w poprzednio wywołanej procedurze bez użycia normalne wywołanie i Konwencji zwracania.

Wywołanie `setjmp` powoduje, że bieżące środowisko stosu do zapisania w *env*. Kolejne wywołanie **longjmp** przywraca zapisane środowisko i zwraca kontrolę do punktu, natychmiast po odpowiednich `setjmp` wywołania. Wznawia wykonywanie tak, jakby *wartość* miał właśnie wrócił przez `setjmp` wywołania. Wartości wszystkich zmiennych (z wyjątkiem zmienne rejestru), które są dostępne do procedury odbieranie kontroli zawierają wartości, kiedy miało **longjmp** została wywołana. Wartości rejestru zmiennych są nieprzewidywalne. Wartość zwrócona przez obiekt `setjmp` musi mieć wartość różną od zera. Jeśli *wartość* jest przekazywany jako 0, wartość 1, zostanie zastąpiony w rzeczywistego zwrotu.

**Microsoft Specific**

W przypadku kodu C++ firmy Microsoft w Windows **longjmp** używa tej samej semantyki odwracania stosu jako kod obsługi wyjątków. Jest bezpieczne do użycia w tych samych miejsc wygenerowany wyjątki C++. Jednak to użycie nie jest przenośny i dołączono niektóre ważne zastrzeżenia.

Wywoływać tylko **longjmp** przed funkcją, która wywołała `setjmp` zwraca; w przeciwnym razie wyniki są nieprzewidywalne.

Sprawdź następujące ograniczenia w przypadku korzystania z **longjmp**:

- Nie należy zakładać, że wartości zmiennych rejestru nie ulegną zmianie. Wartości zmiennych rejestru w rutynowej wywoływania `setjmp` nie mogą być przywracane do odpowiednimi wartościami po **longjmp** jest wykonywany.

- Nie używaj **longjmp** do przekazywania kontroli procedurę obsługi przerwań, chyba że przerwanie jest spowodowane wyjątkiem zmiennoprzecinkowym. W takim przypadku program może zwracać z obsługi przerwań za pośrednictwem **longjmp** Jeśli go najpierw ponownie inicjuje pakiecie zmiennoprzecinkowym zapisu matematycznego, wywołując [_fpreset —](fpreset.md).

- Nie używaj **longjmp** Aby przekazać sterowanie z procedury wywołania zwrotnego wywoływana bezpośrednio lub pośrednio przez kod Windows.

- Jeśli kod jest kompilowany przy użyciu **/EHS** lub **/ehsc** i funkcji, która zawiera **longjmp** wywołanie jest **noexcept** następnie lokalne obiekty w tym, że funkcja nie może zostać zniszczone podczas odwijania stosu.

**END specyficzny dla Microsoft**

> [!NOTE]  
> W przypadku przenośnego kodu C++, nie można zakładać, `setjmp` i `longjmp` obsługują semantyki obiektów języka C++. W szczególności `setjmp` / `longjmp` wywołanie pary ma niezdefiniowane zachowanie, jeśli zastąpienie `setjmp` i `longjmp` przez **catch** i **throw** powodowałoby wywołanie pliku wykonywalnego wszelkie nietrywialnymi destruktory dla obiektów automatycznych. W programach języka C++ zalecane jest używanie mechanizmu obsługi wyjątków C++.

Aby uzyskać więcej informacji, zobacz [przy użyciu funkcji setjmp i longjmp](../../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**longjmp**|\<setjmp.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [_fpreset —](fpreset.md).

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)  
[setjmp](setjmp.md)  
