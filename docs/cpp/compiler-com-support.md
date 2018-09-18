---
title: Obsługa kompilatora COM | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: faab8e0dafdf9121ab694c409500c08aabbb1bc8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079742"
---
# <a name="compiler-com-support"></a>Obsługa kompilatora COM

## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft

Kompilator języka Visual C++ może bezpośrednio odczytywać bibliotek typów model (COM) obiektu składnika i tłumaczy zawartość do kodu źródłowego języka C++, które mogą być zawarte w kompilacji. Rozszerzenia językowe są dostępne dla ułatwienia COM programowanie po stronie klienta.

Za pomocą [#import — dyrektywa preprocesora](../preprocessor/hash-import-directive-cpp.md), kompilator może odczytywać bibliotekę typów i przekonwertować go na plik nagłówka C++, który opisuje COM interfejsy klas. Zbiór `#import` atrybutów jest dostępna dla kontrolki użytkownika zawartości wynikowe pliki nagłówkowe biblioteki typów.

Możesz użyć [__declspec](../cpp/declspec.md) atrybutów rozszerzonych [uuid](../cpp/uuid-cpp.md) można przypisać unikatowy identyfikator globalny (GUID) do obiektu COM. Słowo kluczowe [__uuidof](../cpp/uuidof-operator.md) pozwala wyodrębnić identyfikator GUID skojarzony z obiektem COM. Inny **__declspec** atrybutu [właściwość](../cpp/property-cpp.md), może służyć do określania `get` i `set` metody element członkowski danych obiektu COM.

Zestaw klasy i funkcje globalne obsługi COM znajduje się do obsługi `VARIANT` i `BSTR` typów, implementować inteligentne wskaźniki i hermetyzacji obiekt błędu zgłoszony przez `_com_raise_error`:

- [Funkcje globalne kompilatora COM](../cpp/compiler-com-global-functions.md)

- [_bstr_t](../cpp/bstr-t-class.md)

- [_com_error](../cpp/com-error-class.md)

- [_com_ptr_t](../cpp/com-ptr-t-class.md)

- [_variant_t](../cpp/variant-t-class.md)

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Kompilator klas obsługi COM](../cpp/compiler-com-support-classes.md)<br/>
[Funkcje globalne kompilatora COM](../cpp/compiler-com-global-functions.md)