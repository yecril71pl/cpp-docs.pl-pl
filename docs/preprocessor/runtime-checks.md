---
title: runtime_checks, pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.runtime_checks
- runtime_checks_CPP
helpviewer_keywords:
- runtime_checks pragma
- pragmas, runtime_checks
ms.assetid: ae50b43f-f88d-47ad-a2db-3389e9e7df5b
ms.openlocfilehash: a1c8e6cca27e157818e6ec80182f8fefa112daf1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216607"
---
# <a name="runtime_checks-pragma"></a>runtime_checks, pragma

Wyłącza lub przywraca ustawienia [/RTC](../build/reference/rtc-run-time-error-checks.md) .

## <a name="syntax"></a>Składnia

> **#pragma runtime_checks ("** [ *runtime_checks* ] **",** { **Restore** | **off** } **)**

## <a name="remarks"></a>Uwagi

Nie można włączyć sprawdzania czasu wykonywania, które nie zostało włączone przez opcję kompilatora. Na przykład, jeśli nie zostanie określony `/RTCs` w wierszu polecenia, określenie `#pragma runtime_checks( "s", restore)` nie spowoduje włączenia weryfikacji ramki stosu.

Dyrektywa pragma **runtime_checks** musi znajdować się poza funkcją i zaczyna obowiązywać przy pierwszej funkcji zdefiniowanej po wystąpieniu dyrektywy pragma. Argumenty **Przywróć** i **Wyłącz** zmieniają opcje określone w **runtime_checks** .

**Runtime_checks** może mieć zero lub więcej parametrów przedstawionych w poniższej tabeli.

### <a name="parameters-of-the-runtime_checks-pragma"></a>Parametry dyrektywy pragma runtime_checks

| Parametry | Typ sprawdzania czasu wykonywania |
|--------------------|-----------------------------|
| **s** | Włącza weryfikację stosu (ramki). |
| **c** | Raportuje, gdy wartość jest przypisana do mniejszego typu danych, co powoduje utratę danych. |
| **u** | Raportuje, gdy zmienna jest używana przed zdefiniowaniem. |

Te parametry są takie same, jak te, `/RTC` które są używane z opcją kompilatora. Na przykład:

```cpp
#pragma runtime_checks( "sc", restore )
```

Użycie dyrektywy pragma **runtime_checks** z pustym ciągiem ( **""** ) jest specjalną formą:

- W przypadku użycia parametru **off** włączane są sprawdzanie błędów czasu wykonywania wyszczególnione w powyższej tabeli, off.

- W przypadku użycia parametru **Restore** resetuje sprawdzanie błędów czasu wykonywania do tych, które zostały określone przy użyciu `/RTC` opcji kompilatora.

```cpp
#pragma runtime_checks( "", off )
/* runtime checks are off in this region */
#pragma runtime_checks( "", restore )
```

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
