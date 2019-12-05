---
title: Obsługa kompilatora COM
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
ms.openlocfilehash: 6ab697e5a090158b034a385e60978cff4a73f488
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857583"
---
# <a name="compiler-com-support"></a>Obsługa kompilatora COM

**Microsoft Specific**

Kompilator firmy C++ Microsoft może bezpośrednio odczytywać biblioteki typów modelu COM (Component Object Model) i przetłumaczyć zawartość na C++ kod źródłowy, który może zostać uwzględniony w kompilacji. Rozszerzenia językowe są dostępne, aby ułatwić programowanie COM po stronie klienta dla aplikacji klasycznych.

Za pomocą [dyrektywy preprocesora #import](../preprocessor/hash-import-directive-cpp.md), kompilator może odczytać bibliotekę typów i przekonwertować ją do pliku C++ nagłówkowego opisującego interfejsy com jako klasy. Zestaw atrybutów `#import` jest dostępny dla kontrolki użytkownika zawartości dla plików nagłówkowych biblioteki typów.

Można użyć [__declspec](../cpp/declspec.md) atrybut rozszerzony [UUID](../cpp/uuid-cpp.md) , aby przypisać unikatowy identyfikator globalny (GUID) do obiektu com. Za pomocą słowa kluczowego [__uuidof](../cpp/uuidof-operator.md) można wyodrębnić identyfikator GUID skojarzony z obiektem com. Innym **__declspec** atrybutu, [Property](../cpp/property-cpp.md), można użyć do określenia metod `get` i `set` dla elementu członkowskiego danych obiektu com.

Zestaw globalnych funkcji i klas obsługi modelu COM zapewnia obsługę typów `VARIANT` i `BSTR`, implementowanie inteligentnych wskaźników i Hermetyzowanie obiektu Error zgłoszonego przez `_com_raise_error`:

- [Funkcje globalne kompilatora COM](../cpp/compiler-com-global-functions.md)

- [_bstr_t](../cpp/bstr-t-class.md)

- [_com_error](../cpp/com-error-class.md)

- [_com_ptr_t](../cpp/com-ptr-t-class.md)

- [_variant_t](../cpp/variant-t-class.md)

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Kompilator klas obsługi COM](../cpp/compiler-com-support-classes.md)<br/>
[Funkcje globalne kompilatora COM](../cpp/compiler-com-global-functions.md)
