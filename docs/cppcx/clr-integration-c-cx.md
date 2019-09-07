---
title: Integracja środowiska CLRC++(/CX)
ms.date: 01/22/2017
ms.assetid: 76e213cf-2f3d-4181-b35b-9fd25d5b307c
ms.openlocfilehash: 44ef35d1a62706cae37285c06547a8b9b7deb35c
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740294"
---
# <a name="clr-integration-ccx"></a>Integracja środowiska CLRC++(/CX)

Niektóre typy środowisko wykonawcze systemu Windows otrzymują specjalną obsługę C++w/CX i Języki, które są oparte na środowisku uruchomieniowym języka wspólnego (CLR). W tym artykule omówiono, jak kilka typów w jednym języku jest mapowanych na inny język. Na przykład środowisko CLR mapuje Windows. Foundation. IVector do System. Collections. IList, Windows. Foundation. IMap do System. Collections. IDictionary i tak dalej. Podobnie, C++/CX specjalnie mapuje typy takie jak platforma::D Elegata i platform:: String.

## <a name="mapping-the-windows-runtime-to-ccx"></a>Mapowanie środowisko wykonawcze systemu Windows na C++/CX

Gdy C++/CX odczytuje plik metadanych systemu Windows (WinMD), kompilator automatycznie mapuje typowe środowisko wykonawcze systemu Windows przestrzenie nazw i typów C++do/CX przestrzeni nazw i typów. Na przykład typ `UInt32` liczbowy środowisko wykonawcze systemu Windows jest automatycznie mapowany do `default::uint32`.

C++/CX mapuje kilka innych typów środowisko wykonawcze systemu Windows do przestrzeni nazw **platformy** . Na przykład dojście HString **systemu Windows:: Foundation** , które reprezentuje ciąg tekstowy w formacie Unicode, jest mapowany na klasę C++/CX. `Platform::String` Gdy operacja środowisko wykonawcze systemu Windows zwraca błąd HRESULT, jest mapowana na C++/CX. `Platform::Exception`

C++/CX również mapuje niektóre typy w przestrzeni nazw środowisko wykonawcze systemu Windows, aby zwiększyć funkcjonalność typu. W przypadku tych typów C++/CX dostarcza konstruktorów pomocników i metod, które C++ są specyficzne dla i nie są dostępne w standardowym pliku winmd typu.

Na poniższej liście przedstawiono struktury wartości obsługujące nowe konstruktory i metody pomocnika. Jeśli wcześniej Zapisano kod, który używa list inicjalizacji struktury, zmień go tak, aby korzystał z nowo dodanych konstruktorów.

**Windows::Foundation**

- Moment

- Cinania

- Rozmiar

**Windows:: UI**

- Kolor

**Windows:: UI:: XAML**

- CornerRadius

- Duration

- GridLength

- Grubość

**Windows:: UI:: XAML:: Interop**

- TypeName

**Windows::UI::Xaml::Media**

- Matrix

**Windows:: UI:: XAML:: Media:: Animation**

- KeyTime

- RepeatBehavior

**Windows::UI::Xaml::Media::Media3D**

- Matrix3D

## <a name="mapping-the-clr-to-ccx"></a>Mapowanie środowiska CLR do C++/CX

Gdy firma Microsoft C++ lub C# kompilatory odczytują plik winmd, automatycznie mapują pewne typy w pliku metadanych na odpowiednie C++typy/CX lub CLR. Na przykład w środowisku CLR interfejs IVector\<T > jest mapowany na IList\<T >. Jednak w C++/CX interfejs IVector\<> T nie jest zamapowany na inny typ.

IReference\<t > w środowisko wykonawcze systemu Windows mapy do wartości null\<t > na platformie .NET.

## <a name="see-also"></a>Zobacz także

[Współdziałanie z innymi językami](../cppcx/interoperating-with-other-languages-c-cx.md)
