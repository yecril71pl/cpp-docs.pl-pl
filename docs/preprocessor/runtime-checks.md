---
title: runtime_checks
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.runtime_checks
- runtime_checks_CPP
helpviewer_keywords:
- runtime_checks pragma
- pragmas, runtime_checks
ms.assetid: ae50b43f-f88d-47ad-a2db-3389e9e7df5b
ms.openlocfilehash: 38df7ccc384830bb547c11e1a3d5458a1298574c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547371"
---
# <a name="runtimechecks"></a>runtime_checks
Wyłącza lub przywraca [usunęliśmy](../build/reference/rtc-run-time-error-checks.md) ustawienia.

## <a name="syntax"></a>Składnia

```
#pragma runtime_checks( "[runtime_checks]", {restore | off} )
```

## <a name="remarks"></a>Uwagi

Nie można włączyć sprawdzanie w czasie wykonania, która nie została włączona przy użyciu opcji kompilatora. Na przykład, jeśli nie określisz `/RTCs`, określanie `#pragma runtime_checks( "s", restore)` nie umożliwi Weryfikacja ramki stosu.

**Runtime_checks** pragma musi znajdować się poza funkcją i zaczyna obowiązywać przy pierwszej funkcji zdefiniowanych po pragmy jest widoczny. *Przywrócić* i *poza* argumenty Włącz opcje określone w **runtime_checks** lub wyłączyć.

**Runtime_checks** może być zero lub jeden z parametrów pokazano w poniższej tabeli.

### <a name="parameters-of-the-runtimechecks-pragma"></a>Parametry runtime_checks Pragma

|Parametry|Typ kontroli czasu wykonywania|
|--------------------|-----------------------------|
|*s*|Włącza stosu (ramek) weryfikacji.|
|*c*|Raporty, gdy wartość jest przypisany do mniejszego typu danych, które powoduje utratę danych.|
|*u*|Raporty, gdy zmienna jest używana, zanim zostanie on zdefiniowany.|

Są to tych samych liter, w ramach `/RTC` — opcja kompilatora. Na przykład:

```
#pragma runtime_checks( "sc", restore )
```

Za pomocą **runtime_checks** dyrektywę pusty ciąg (**""**) jest specjalną forma dyrektywy:

- Kiedy używasz *poza* parametru włącza sprawdzanie błędów czasu wykonywania, wymienione w powyższej tabeli, wyłącz.

- Kiedy używasz *przywrócić* parametru resetuje sprawdzanie błędów czasu wykonywania do tych, które określone z `/RTC` — opcja kompilatora.

```
#pragma runtime_checks( "", off )
.
.
.
#pragma runtime_checks( "", restore )
```

## <a name="see-also"></a>Zobacz też

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)