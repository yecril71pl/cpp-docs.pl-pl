---
title: no_auto_exclude — atrybut importowania
ms.date: 08/29/2019
f1_keywords:
- no_auto_exclude
helpviewer_keywords:
- no_auto_exclude attribute
ms.assetid: 3241ef9c-758a-4e86-bdc5-37da6072430f
ms.openlocfilehash: 530c2b2adf24e964cb0a512371f4430a61bf8b11
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216080"
---
# <a name="no_auto_exclude-import-attribute"></a>no_auto_exclude — atrybut importowania

**C++Specjalne**

Wyłącza automatyczne wykluczenie.

## <a name="syntax"></a>Składnia

> **#import** *Biblioteka typów* **no_auto_exclude**

## <a name="remarks"></a>Uwagi

Biblioteki typów mogą zawierać definicje elementów zdefiniowanych w nagłówkach systemowych lub innych bibliotekach typów. `#import`próbuje uniknąć wielu błędów definicji przez automatyczne wyłączenie takich elementów. Powoduje to wystawienie [ostrzeżenia kompilatora (poziom 3)](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md) dla każdego elementu, który ma zostać wykluczony. Można wyłączyć automatyczne wykluczenie przy użyciu tego atrybutu.

**ZAKOŃCZENIE C++ określonych**

## <a name="see-also"></a>Zobacz także

[Atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)
