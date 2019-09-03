---
title: no_smart_pointers — atrybut importowania
ms.date: 08/29/2019
f1_keywords:
- no_smart_pointers
helpviewer_keywords:
- no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
ms.openlocfilehash: 1fca3eb486ff3cfc7403c38e91855b799a698782
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220698"
---
# <a name="no_smart_pointers-import-attribute"></a>no_smart_pointers — atrybut importowania

**C++Specjalne**

Pomija Tworzenie inteligentnych wskaźników dla wszystkich interfejsów w bibliotece typów.

## <a name="syntax"></a>Składnia

> **#import** *Biblioteka typów* **no_smart_pointers**

## <a name="remarks"></a>Uwagi

Domyślnie, gdy `#import`używasz, uzyskujesz deklarację inteligentnego wskaźnika dla wszystkich interfejsów w bibliotece typów. Te inteligentne wskaźniki są typu [_com_ptr_t](../cpp/com-ptr-t-class.md).

**ZAKOŃCZENIE C++ określonych**

## <a name="see-also"></a>Zobacz także

[Atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)
