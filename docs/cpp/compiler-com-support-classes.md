---
title: Kompilator klas obsługi COM
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
ms.openlocfilehash: 1a9ff7c57965c9ba00881d5fe48501a6138b31d1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444421"
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