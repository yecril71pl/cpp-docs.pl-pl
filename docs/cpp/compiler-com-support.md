---
title: Obsługa kompilatora COM
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
ms.openlocfilehash: 9a5961049cbc54c94cec5b444e2d98f013dda932
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233785"
---
# <a name="compiler-com-support"></a>Obsługa kompilatora COM

**Specyficzne dla firmy Microsoft**

Kompilator języka Microsoft C++ może bezpośrednio odczytywać biblioteki typów modelu COM (Component Object Model) i przetłumaczyć zawartość na kod źródłowy języka C++, który może zostać uwzględniony w kompilacji. Rozszerzenia językowe są dostępne, aby ułatwić programowanie COM po stronie klienta dla aplikacji klasycznych.

Za pomocą [dyrektywy preprocesora #import](../preprocessor/hash-import-directive-cpp.md), kompilator może odczytać bibliotekę typów i przekonwertować ją do pliku nagłówkowego C++ opisującego interfejsy com jako klasy. Zestaw `#import` atrybutów jest dostępny dla kontrolki użytkownika zawartości dla plików nagłówkowych biblioteki typów.

Można użyć [__declspec](../cpp/declspec.md) atrybut rozszerzony [UUID](../cpp/uuid-cpp.md) , aby przypisać unikatowy identyfikator globalny (GUID) do obiektu com. Za pomocą słowa kluczowego [__uuidof](../cpp/uuidof-operator.md) można wyodrębnić identyfikator GUID skojarzony z obiektem com. Innym **`__declspec`** atrybutem, [Właściwość](../cpp/property-cpp.md), można użyć do określenia `get` metod i `set` dla elementu członkowskiego danych obiektu com.

Zestaw globalnych funkcji i klas obsługi modelu COM zapewnia obsługę `VARIANT` `BSTR` typów i, implementowanie inteligentnych wskaźników oraz Hermetyzowanie obiektu błędu zgłoszonego przez `_com_raise_error` :

- [Funkcje globalne kompilatora COM](../cpp/compiler-com-global-functions.md)

- [_bstr_t](../cpp/bstr-t-class.md)

- [_com_error](../cpp/com-error-class.md)

- [_com_ptr_t](../cpp/com-ptr-t-class.md)

- [_variant_t](../cpp/variant-t-class.md)

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Klasy obsługi kompilatora COM](../cpp/compiler-com-support-classes.md)<br/>
[Funkcje globalne kompilatora COM](../cpp/compiler-com-global-functions.md)
