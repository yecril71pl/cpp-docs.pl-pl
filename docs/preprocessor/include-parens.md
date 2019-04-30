---
title: include()
ms.date: 10/18/2018
f1_keywords:
- include()
helpviewer_keywords:
- include() attribute
ms.assetid: 86c9dcb2-d9e0-4fd5-97d7-0bb3e23d6ecc
ms.openlocfilehash: 1208f14a9f6b3724dd5353df57213baa3910d07f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383740"
---
# <a name="include"></a>include()

**Określonego język C++**

Wyłącza automatyczne wykluczenia.

## <a name="syntax"></a>Składnia

```
include("Name1"[,"Name2", ...])
```

### <a name="parameters"></a>Parametry

*Nazwa1*<br/>
Pierwszy element wymuszone dołączenia.

*Nazwa2*<br/>
Drugi element do uwzględnienia wymuszone (jeśli jest to konieczne).

## <a name="remarks"></a>Uwagi

Biblioteki typów mogą obejmować definicje elementy zdefiniowane w nagłówkach systemu lub inne biblioteki typów. `#import` próbuje uniknąć wiele błędów definicji wykluczając automatycznie takie elementy. Jeśli elementy zostały wyłączone, wskazane przez [ostrzeżenie kompilatora (poziom 3) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md), i nie powinny mieć been, ten atrybut można wyłączyć automatyczne wykluczenia. Ten atrybut może być dowolną liczbę argumentów, każda z nich nazwę element biblioteki typów które mają zostać uwzględnione.

**KONIEC określonego języka C++**

## <a name="see-also"></a>Zobacz także

[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import Directive](../preprocessor/hash-import-directive-cpp.md)