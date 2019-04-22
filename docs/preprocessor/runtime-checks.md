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
ms.openlocfilehash: 44c26fb90a2d2f9ba78ec7dba7cceed65a4b4ed7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59027086"
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

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)