---
title: high_property_prefixes — atrybut importowania
ms.date: 08/29/2019
f1_keywords:
- high_property_prefixes
helpviewer_keywords:
- high_property_prefixes attribute
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
ms.openlocfilehash: 9e44f6f1afae479f803f4c6d866ef3ee38744561
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219000"
---
# <a name="high_property_prefixes-import-attribute"></a>high_property_prefixes — atrybut importowania

**C++Specjalne**

Określa alternatywne prefiksy dla trzech metod właściwości.

## <a name="syntax"></a>Składnia

> **#import** *Biblioteka typów* **high_property_prefixes (** "*getprefix*" **,** "*PutPrefix*" **,** "*PutRefPrefix*" **)**

### <a name="parameters"></a>Parametry

*Getprefix*\
Prefiks, `propget` który ma być używany dla metod.

*PutPrefix*\
Prefiks, `propput` który ma być używany dla metod.

*PutRefPrefix*\
Prefiks, `propputref` który ma być używany dla metod.

## <a name="remarks"></a>Uwagi

`propget`Domyślnie metody obsługi błędów wysokiego poziomu, `propput`, i `propputref` są uwidaczniane przez funkcje Członkowskie o nazwach z prefiksami `Get`, `Put`i `PutRef`, odpowiednio.

**ZAKOŃCZENIE C++ określonych**

## <a name="see-also"></a>Zobacz także

[Atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)
