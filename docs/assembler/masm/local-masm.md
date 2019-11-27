---
title: LOCAL (MASM)
ms.date: 08/30/2018
f1_keywords:
- Local
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
ms.openlocfilehash: c3a04f68b7fd17b2b6459c219a98fd99ec2d62d4
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397252"
---
# <a name="local-masm"></a>LOCAL (MASM)

W pierwszej dyrektywie w makrze **lokalna** definiuje etykiety, które są unikatowe dla każdego wystąpienia makra.

## <a name="syntax"></a>Składnia

> **Local** *LocalName* ⟦, *LocalName* ... ⟧
>
> **Lokalna** *etykieta* ⟦ *Liczba*\[ __]__ ⟧ ⟦ __:__ *Typ*⟧ ⟦ __,__ *etykieta* ⟦ __\[__ *Count* __]__ ⟧ ⟦*Type*⟧... ⟧

## <a name="remarks"></a>Uwagi

W drugiej dyrektywie, w ramach definicji procedury (**proc**), **lokalna** tworzy zmienne oparte na stosie, które istnieją na czas trwania tej procedury. *Etykieta* może być prostą zmienną lub tablicą zawierającą elementy *Count* .

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)
