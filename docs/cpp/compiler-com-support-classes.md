---
title: Kompilator klas obsługi COM
ms.date: 11/04/2016
f1_keywords:
- _com_raise_error
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
ms.openlocfilehash: 066fe797bc500625e96e027777a70f278b88cddb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479667"
---
# <a name="compiler-com-support-classes"></a>Kompilator klas obsługi COM

**Microsoft Specific**

Standardowych klas są używane do obsługi niektórych typów modelu COM. Klasy są zdefiniowane w \<comdef.h > i pliki nagłówkowe wygenerowane z biblioteki typów.

|Class|Cel|
|-----------|-------------|
|[_bstr_t](../cpp/bstr-t-class.md)|Opakowuje `BSTR` typu przydatne operatory i metody.|
|[_com_error](../cpp/com-error-class.md)|Definiuje obiekt błędu zgłoszony przez [_com_raise_error —](../cpp/com-raise-error.md) w większości błędów.|
|[_com_ptr_t](../cpp/com-ptr-t-class.md)|Hermetyzuje wskaźniki interfejsu COM i automatyzuje wymaganego wywołania `AddRef`, `Release`, i `QueryInterface`.|
|[_variant_t](../cpp/variant-t-class.md)|Opakowuje `VARIANT` typu przydatne operatory i metody.|

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Obsługa kompilatora COM](../cpp/compiler-com-support.md)<br/>
[Funkcje globalne kompilatora COM](../cpp/compiler-com-global-functions.md)<br/>
[Dokumentacja języka C++](../cpp/cpp-language-reference.md)