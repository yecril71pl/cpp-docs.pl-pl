---
title: raw_interfaces_only — atrybut importowania
ms.date: 08/29/2019
f1_keywords:
- raw_interfaces_only
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
ms.openlocfilehash: 4b79aa4dbafa204d84f4d6ed7ec78fdec1b81fa7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216208"
---
# <a name="raw_interfaces_only-import-attribute"></a>raw_interfaces_only — atrybut importowania

**C++Specjalne**

Pomija generowanie funkcji otoki obsługujących błędy i deklaracji [Właściwości](../cpp/property-cpp.md) , które korzystają z tych funkcji otoki.

## <a name="syntax"></a>Składnia

> **#import** *Biblioteka typów* **raw_interfaces_only**

## <a name="remarks"></a>Uwagi

Atrybut **raw_interfaces_only** powoduje również, że domyślny prefiks używany do nadawania nazw funkcji niebędących właściwościami do usunięcia. Zwykle prefiks jest `raw_`. Jeśli ten atrybut jest określony, nazwy funkcji są pobierane bezpośrednio z biblioteki typów.

Ten atrybut umożliwia uwidocznienie tylko zawartości niskiego poziomu w bibliotece typów.

**ZAKOŃCZENIE C++ określonych**

## <a name="see-also"></a>Zobacz także

[Atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)
