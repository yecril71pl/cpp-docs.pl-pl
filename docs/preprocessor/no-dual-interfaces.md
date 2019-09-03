---
title: no_dual_interfaces — atrybut importowania
ms.date: 08/29/2019
f1_keywords:
- no_dual_interfaces
helpviewer_keywords:
- no_dual_interfaces attribute
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
ms.openlocfilehash: 6270888f0d31e4fbe18fb3364995be8c73426b83
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220761"
---
# <a name="no_dual_interfaces-import-attribute"></a>no_dual_interfaces — atrybut importowania

**C++Specjalne**

Zmienia sposób, w jaki kompilator generuje funkcje otoki dla dwóch metod interfejsu.

## <a name="syntax"></a>Składnia

> **#import** *Biblioteka typów* **no_dual_interfaces**

## <a name="remarks"></a>Uwagi

Zwykle otoka wywołuje metodę za pomocą tabeli funkcji wirtualnych dla interfejsu. W przypadku elementu **no_dual_interfaces**otoka wywołuje `IDispatch::Invoke` wywołanie metody.

**ZAKOŃCZENIE C++ określonych**

## <a name="see-also"></a>Zobacz także

[Atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)
