---
title: Integracja środowiska CLR (C + +/ CX)
ms.date: 01/22/2017
ms.assetid: 76e213cf-2f3d-4181-b35b-9fd25d5b307c
ms.openlocfilehash: df0c5e9cfaf9a4148c8d16b68ee04b4e9ce82e6a
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749026"
---
# <a name="clr-integration-ccx"></a>Integracja środowiska CLR (C + +/ CX)

Niektórych typów środowiska wykonawczego Windows otrzymywać specjalnej obsługi w języku C + +/ CX i języki, które opierają się na środowisko uruchomieniowe języka wspólnego (CLR). W tym artykule omówiono sposób kilka typów w jednym języku mapowania na inny język. Na przykład środowisko CLR mapuje Windows.Foundation.IVector System.Collections.IList, Windows.Foundation.IMap System.Collections.IDictionary i tak dalej. Podobnie, C + +/ CX specjalnie mapowania typów, takich jak Platform::Delegate i Platform::String.

## <a name="mapping-the-windows-runtime-to-ccx"></a>Mapowania środowiska wykonawczego Windows w języku C + +/ CX

Gdy C + +/ CX odczytuje plik metadanych (.winmd) Windows, kompilator automatycznie mapuje wspólnego środowiska uruchomieniowego Windows obszary nazw i typy dla C + +/ CX przestrzenie nazw i typów. Na przykład Windows Runtime typu liczbowego `UInt32` jest automatycznie mapowany `default::uint32`.

C + +/ CX mapuje kilka innych typów środowiska wykonawczego Windows, aby **platformy** przestrzeni nazw. Na przykład **Windows::Foundation** dojścia HSTRING, który reprezentuje tylko do odczytu ciąg tekstowy Unicode, jest mapowany na C + +/ CX `Platform::String` klasy. Podczas operacji Windows Runtime zwraca błąd HRESULT, jest zamapowana w języku C + +/ CX `Platform::Exception`.

C + +/ CX mapuje również niektóre typy w przestrzeniach nazw środowiska wykonawczego Windows, aby zwiększyć funkcji typu. W przypadku tych typów C + +/ CX zapewnia pomocnika konstruktorów i metod, które są specyficzne dla języka C++ i nie są dostępne w pliku winmd standardowego typu.

Poniższej przedstawiono struktury wartości, które obsługują nowe konstruktory i metody pomocnicze. Jeśli zostały wcześniej napisany kod, który używa listy inicjowania struktury, zmień go do korzystania z nowo dodanym konstruktorów.

**Windows::Foundation**

- Punkt

- Rect

- Rozmiar

**Windows::UI**

- Kolor

**Windows::UI::Xaml**

- CornerRadius

- Czas trwania

- GridLength

- Grubość

**Windows::UI::Xaml::Interop**

- TypeName

**Windows::UI::Xaml::Media**

- Matrix

**Windows::UI::Xaml::Media::Animation**

- KeyTime

- RepeatBehavior

**Windows::UI::Xaml::Media::Media3D**

- Matrix3D

## <a name="mapping-the-clr-to-ccx"></a>Mapowanie środowiska CLR dla C + +/ CX

Jeśli Kompilatory języka Visual C++ lub C# do odczytu pliku winmd, automatycznie mapują niektórych typów w pliku metadanych dla odpowiedniego języka C + +/ CX lub CLR typów. Na przykład w CLR, IVector\<T > Interfejs jest mapowany na IList\<T >. Ale w języku C + +/ CX, IVector\<T > Interfejs nie jest zamapowany do innego typu.

IReference\<T > w środowisku uruchomieniowym Windows mapuje Nullable\<T > na platformie .NET.

## <a name="see-also"></a>Zobacz także

[Współdziałanie z innymi językami](../cppcx/interoperating-with-other-languages-c-cx.md)
