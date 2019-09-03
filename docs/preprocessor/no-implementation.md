---
title: no_implementation — atrybut importowania
ms.date: 08/29/2019
f1_keywords:
- no_implementation
helpviewer_keywords:
- no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
ms.openlocfilehash: 8f0a7454fdbedc1959b665ccb2a23748d21c342d
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220770"
---
# <a name="no_implementation-import-attribute"></a>no_implementation — atrybut importowania

**C++Specjalne**

Pomija generowanie `.tli` nagłówka, który zawiera implementacje funkcji elementu członkowskiego otoki.

## <a name="syntax"></a>Składnia

> **#import** *Biblioteka typów* **no_implementation**

## <a name="remarks"></a>Uwagi

Jeśli ten atrybut jest określony, `.tlh` nagłówek wraz z deklaracjami do udostępnienia elementów biblioteki typów, zostanie wygenerowany `#include` bez instrukcji, aby dołączyć `.tli` plik nagłówka.

Ten atrybut jest używany w połączeniu z [implementation_only](../preprocessor/implementation-only.md).

**ZAKOŃCZENIE C++ określonych**

## <a name="see-also"></a>Zobacz także

[Atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)
