---
title: Kompilator klas obsługi COM
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
ms.openlocfilehash: a8b0845fdfa96c1cb4b8b67e9d39169d9f4d3737
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189705"
---
# <a name="compiler-com-support-classes"></a>Kompilator klas obsługi COM

**Specyficzne dla firmy Microsoft**

Klasy standardowe są używane do obsługi niektórych typów modelu COM. Klasy są zdefiniowane w \<comdef. h > i plików nagłówkowych wygenerowanych z biblioteki typów.

|Klasa|Przeznaczenie|
|-----------|-------------|
|[_bstr_t](../cpp/bstr-t-class.md)|Zawija typ `BSTR`, aby zapewnić użyteczne operatory i metody.|
|[_com_error](../cpp/com-error-class.md)|Definiuje obiekt błędu zgłoszony przez [_com_raise_error](../cpp/com-raise-error.md) w większości błędów.|
|[_com_ptr_t](../cpp/com-ptr-t-class.md)|Hermetyzuje wskaźniki interfejsów COM i automatyzuje wymagane wywołania do `AddRef`, `Release`i `QueryInterface`.|
|[_variant_t](../cpp/variant-t-class.md)|Zawija typ `VARIANT`, aby zapewnić użyteczne operatory i metody.|

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Obsługa kompilatora COM](../cpp/compiler-com-support.md)<br/>
[Funkcje globalne kompilatora COM](../cpp/compiler-com-global-functions.md)<br/>
[Dokumentacja języka C++](../cpp/cpp-language-reference.md)
