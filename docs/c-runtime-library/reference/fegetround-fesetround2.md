---
title: fegetround, fesetround
ms.date: 04/05/2018
apiname:
- fegetround
- fesetround
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fegetround
- fesetround
- fenv/fegetround
- fenv/fesetround
helpviewer_keywords:
- fegetround function
- fesetround function
ms.assetid: 596af00b-be2f-4f57-b2f5-460485f9ff0b
ms.openlocfilehash: 061f0c9563d284396e85c6de70a2fe0911218eb3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666807"
---
# <a name="fegetround-fesetround"></a>fegetround, fesetround

Pobiera lub ustawia bieżący tryb zaokrąglania zmiennoprzecinkowych.

## <a name="syntax"></a>Składnia

```C
int fegetround(void);

int fesetround(
   int round_mode
);
```

### <a name="parameters"></a>Parametry

*round_mode*<br/>
Tryb zaokrąglania można ustawić jako jeden z zmiennoprzecinkowych makra zaokrąglania. Jeśli wartość nie jest równa jeden zmiennoprzecinkowych makra zaokrąglania, tryb zaokrąglania nie jest zmieniany.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia **fegetround** zwraca trybu zaokrąglania jako jeden z zmiennoprzecinkowej zaokrąglania wartości makra. Jeśli bieżący tryb zaokrąglania nie może być określony, zwraca wartość ujemną.

W przypadku powodzenia **fesetround** zwraca wartość 0. W przeciwnym razie zostanie zwrócona wartość różna od zera.

## <a name="remarks"></a>Uwagi

Operacji zmiennoprzecinkowych można użyć jednego z kilku trybów zaokrąglania. Te kontroluje kierunek, w którym wyniki operacji zmiennoprzecinkowych jest zaokrąglana w kierunku gdy wyniki są przechowywane. Oto nazwy i zachowania zmiennoprzecinkowego zaokrąglania makra zdefiniowane w \<fenv.h >:

|Macro|Opis|
|-----------|-----------------|
|FE_DOWNWARD|Zaokrąglij w kierunku minus nieskończoność.|
|FE_TONEAREST|Zaokrąglony do najbliższej wartości.|
|FE_TOWARDZERO|Zaokrąglij w kierunku zera.|
|FE_UPWARD|Zaokrąglij w kierunku nieskończoności dodatniej.|

Domyślne zachowanie FE_TONEAREST jest zaokrąglona wyniki połowie między reprezentowanych wartości do najbliższej wartości z nawet (0) najmniej znaczący bit.

Bieżący tryb zaokrąglania ma wpływ na następujące operacje:

- Ciąg konwersje.

- Wyniki zmiennoprzecinkowych operatorów arytmetycznych poza wyrażeń stałych.

- Biblioteka zaokrąglania funkcje, takie jak **rukuj** i **nearbyint —**.

- Wartości zwracane przez funkcje matematyczne biblioteki standardowej.

Bieżący tryb zaokrąglania nie ma wpływu na te operacje:

- **Trunc**, **ceil —**, **floor**, i **lround —** funkcji biblioteki.

- Zmiennoprzecinkowe do liczby całkowitej niejawne rzutowanie i konwersje, które zawsze zaokrąglanie w kierunku zera.

- Wyniki zmiennoprzecinkowych operatorów arytmetycznych w wyrażeniu stałym, które zawsze zaokrąglona do najbliższej wartości.

Aby korzystać z tych funkcji, należy wyłączyć funkcję optymalizacji zmiennopozycyjnych, które mogą uniemożliwić dostęp przy użyciu `#pragma fenv_access(on)` dyrektywy przed wywołaniem. Aby uzyskać więcej informacji, zobacz [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek języka C++|
|--------------|--------------|------------------|
|**fegetround**, **fesetround**|\<fenv.h>|\<cfenv>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[nearbyint —, nearbyintf —, nearbyintl](nearbyint-nearbyintf-nearbyintl1.md)<br/>
[rint, rintf, rintl](rint-rintf-rintl.md)<br/>
[lrint, lrintf, lrintl, llrint, llrintf, llrintl](lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)<br/>
