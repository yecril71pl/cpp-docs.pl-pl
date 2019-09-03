---
title: Wyklucz Importowanie atrybutu
ms.date: 08/29/2019
f1_keywords:
- exclude
helpviewer_keywords:
- exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
ms.openlocfilehash: 6a3625ee0dd44f3e2731e1240fea5f3dd4ed109e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218720"
---
# <a name="exclude-import-attribute"></a>Wyklucz Importowanie atrybutu

**C++Specjalne**

Wyklucza elementy z generowanych plików nagłówkowych biblioteki typów.

## <a name="syntax"></a>Składnia

> **#import** *Biblioteka typów* **exclude (** "*Name1*" [ **,** "*NAME2*"...] **)**

### <a name="parameters"></a>Parametry

*Name1*\
Pierwszy element, który ma zostać wykluczony.

*NAME2*\
Obowiązkowe Elementy sekundowe i późniejsze do wykluczenia, w razie potrzeby.

## <a name="remarks"></a>Uwagi

Biblioteki typów mogą zawierać definicje elementów zdefiniowanych w nagłówkach systemowych lub innych bibliotekach typów. Ten atrybut może przyjmować dowolną liczbę argumentów, gdzie każda z nich jest elementem biblioteki typu najwyższego poziomu, który ma zostać wykluczony.

**ZAKOŃCZENIE C++ określonych**

## <a name="see-also"></a>Zobacz także

[Atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)
