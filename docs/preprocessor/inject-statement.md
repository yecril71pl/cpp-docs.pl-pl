---
title: inject_statement — atrybut importowania
ms.date: 08/29/2019
f1_keywords:
- inject_statement
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
ms.openlocfilehash: 25dee621ff8af2c9a39e605b9da2c29d80f9570a
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220994"
---
# <a name="inject_statement-import-attribute"></a>inject_statement — atrybut importowania

**C++Specjalne**

Wstawia swój argument jako tekst źródłowy do nagłówka biblioteki typów.

## <a name="syntax"></a>Składnia

> **#import** *Biblioteka typów* **inject_statement (** "*Źródło tekstu*" **)**

### <a name="parameters"></a>Parametry

*tekst źródłowy*\
Tekst źródłowy, który ma zostać wstawiony do pliku nagłówkowego biblioteki typów.

## <a name="remarks"></a>Uwagi

Tekst jest umieszczany na początku deklaracji przestrzeni nazw, która otacza zawartość *biblioteki typów* w pliku nagłówkowym.

**ZAKOŃCZENIE C++ określonych**

## <a name="see-also"></a>Zobacz także

[Atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)
