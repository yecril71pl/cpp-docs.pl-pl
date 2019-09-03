---
title: no_namespace — atrybut importowania
ms.date: 08/29/2019
f1_keywords:
- no_namespace
helpviewer_keywords:
- no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
ms.openlocfilehash: ba52aed69cdbb46c135e6de5078d718e93f99c87
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220739"
---
# <a name="no_namespace-import-attribute"></a>no_namespace — atrybut importowania

**C++Specjalne**

Określa, że kompilator nie generuje nazwy przestrzeni nazw.

## <a name="syntax"></a>Składnia

> **#import** *Biblioteka typów* **no_namespace**

## <a name="remarks"></a>Uwagi

Zawartość biblioteki typów w `#import` pliku nagłówkowym są zwykle zdefiniowane w przestrzeni nazw. Nazwa przestrzeni nazw jest określona w `library` instrukcji oryginalnego pliku IDL. Jeśli atrybut **no_namespace** jest określony, ta przestrzeń nazw nie jest generowana przez kompilator.

Jeśli chcesz użyć innej nazwy przestrzeni nazw, zamiast tego użyj atrybutu [rename_namespace](../preprocessor/rename-namespace.md) .

**ZAKOŃCZENIE C++ określonych**

## <a name="see-also"></a>Zobacz także

[Atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)
