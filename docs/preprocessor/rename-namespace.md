---
title: rename_namespace — atrybut importowania
ms.date: 08/29/2019
f1_keywords:
- rename_namespace
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
ms.openlocfilehash: d319d7390e7c7dce070a35be44aad37c7a34e1a0
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216653"
---
# <a name="rename_namespace-import-attribute"></a>rename_namespace — atrybut importowania

**C++Specjalne**

Zmienia nazwę przestrzeni nazw, która zawiera zawartość biblioteki typów.

## <a name="syntax"></a>Składnia

> **#import** *Biblioteka typów* **rename_namespace (** "*newname*" **)**

### <a name="parameters"></a>Parametry

*NewName*\
Nowa nazwa przestrzeni nazw.

## <a name="remarks"></a>Uwagi

Atrybut **rename_namespace** przyjmuje jeden argument, *nowa_nazwa*, który określa nową nazwę przestrzeni nazw.

Aby usunąć przestrzeń nazw, zamiast tego należy użyć atrybutu [no_namespace](../preprocessor/no-namespace.md) .

**ZAKOŃCZENIE C++ określonych**

## <a name="see-also"></a>Zobacz także

[Atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)
