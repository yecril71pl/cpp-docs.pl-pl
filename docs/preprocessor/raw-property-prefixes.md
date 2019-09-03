---
title: raw_property_prefixes — atrybut importowania
ms.date: 08/29/2019
f1_keywords:
- raw_property_prefixes
helpviewer_keywords:
- raw_property_prefixes attribute
ms.assetid: 03a0f48c-c460-4175-a762-9f7f8d84b12f
ms.openlocfilehash: d4d91470781e7c5f673fd228c24904322d1db8b3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216036"
---
# <a name="raw_property_prefixes-import-attribute"></a>raw_property_prefixes — atrybut importowania

**C++Specjalne**

Określa alternatywne prefiksy dla trzech metod właściwości.

## <a name="syntax"></a>Składnia

> **#import** *Biblioteka typów* **raw_property_prefixes (** "*getprefix*" **,** "*PutPrefix*" **,** "*PutRefPrefix*" **)**

### <a name="parameters"></a>Parametry

*Getprefix*\
Prefiks do użycia dla `propget` metod.

*PutPrefix*\
Prefiks do użycia dla `propput` metod.

*PutRefPrefix*\
Prefiks do użycia dla `propputref` metod.

## <a name="remarks"></a>Uwagi

Domyślnie, metody niskiego poziomu `propget`, `propput`i `propputref` są uwidaczniane `get_`przez funkcje Członkowskie o nazwach za pomocą prefiksów `put_`, i `putref_`, odpowiednio. Te prefiksy są zgodne z nazwami używanymi w plikach nagłówkowych generowanych przez MIDL.

**ZAKOŃCZENIE C++ określonych**

## <a name="see-also"></a>Zobacz także

[Atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)
