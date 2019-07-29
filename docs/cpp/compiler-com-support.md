---
title: Obsługa kompilatora COM
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
ms.openlocfilehash: 421930088dcbf9762d50b5af37d994b9008890eb
ms.sourcegitcommit: 720b74dddb1cdf4e570d55103158304ee1df81f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/29/2019
ms.locfileid: "68606379"
---
# <a name="compiler-com-support"></a>Obsługa kompilatora COM

## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft

Kompilator firmy C++ Microsoft może bezpośrednio odczytywać biblioteki typów modelu COM (Component Object Model) i przetłumaczyć zawartość na C++ kod źródłowy, który może zostać uwzględniony w kompilacji. Rozszerzenia językowe są dostępne, aby ułatwić programowanie COM po stronie klienta dla aplikacji klasycznych.

Za pomocą [dyrektywy preprocesora #import](../preprocessor/hash-import-directive-cpp.md), kompilator może odczytać bibliotekę typów i przekonwertować ją do pliku C++ nagłówkowego opisującego interfejsy com jako klasy. Zestaw `#import` atrybutów jest dostępny dla kontrolki użytkownika zawartości dla plików nagłówkowych biblioteki typów.

Aby przypisać unikatowy identyfikator globalny (GUID) do obiektu COM, można użyć atrybutu [__declspec](../cpp/declspec.md) o rozszerzeniu [UUID](../cpp/uuid-cpp.md) . Za pomocą słowa kluczowego [__uuidof](../cpp/uuidof-operator.md) można wyodrębnić identyfikator GUID skojarzony z obiektem com. Innym atrybutem **__declspec** , [Property](../cpp/property-cpp.md)można użyć `get` do określenia metod i `set` dla elementu członkowskiego danych obiektu com.

Zestaw globalnych funkcji i klas obsługi modelu com zapewnia obsługę `VARIANT` typów i `BSTR` , implementowanie inteligentnych wskaźników oraz Hermetyzowanie obiektu błędu zgłoszonego przez `_com_raise_error`:

- [Funkcje globalne kompilatora COM](../cpp/compiler-com-global-functions.md)

- [_bstr_t](../cpp/bstr-t-class.md)

- [_com_error](../cpp/com-error-class.md)

- [_com_ptr_t](../cpp/com-ptr-t-class.md)

- [_variant_t](../cpp/variant-t-class.md)

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Kompilator klas obsługi COM](../cpp/compiler-com-support-classes.md)<br/>
[Funkcje globalne kompilatora COM](../cpp/compiler-com-global-functions.md)
