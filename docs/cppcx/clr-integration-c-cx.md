---
title: Integrację środowiska CLR (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 76e213cf-2f3d-4181-b35b-9fd25d5b307c
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 50b455bd3b6fd4a96c3181b60904cb7a3250e866
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33086899"
---
# <a name="clr-integration-ccx"></a>Integrację środowiska CLR (C + +/ CX)
Niektóre typy środowiska wykonawczego systemu Windows odbierania specjalnej obsługi w języku C + +/ CX oraz języki, które są oparte na środowisko uruchomieniowe języka wspólnego (CLR). W tym artykule opisano, jak kilka typów w jednym języku mapować do innego języka. Na przykład CLR mapuje Windows.Foundation.IVector interfejs System.Collections.IList, Windows.Foundation.IMap System.Collections.IDictionary i tak dalej. Podobnie, C + +/ CX specjalnie mapowania typów, takie jak Platform::Delegate i Platform::String.  
  
## <a name="mapping-the-windows-runtime-to-ccx"></a>Mapowanie środowiska uruchomieniowego systemu Windows w języku C + +/ CX  
 Gdy C + +/ CX odczytuje plik metadanych (.winmd) systemu Windows, kompilator automatycznie mapuje wspólne środowiska wykonawczego systemu Windows obszary nazw i typy dla C + +/ CX obszary nazw i typów. Na przykład liczbowego typu środowiska wykonawczego systemu Windows `UInt32` jest automatycznie mapowany `default::uint32`.  
  
 C + +/ CX mapuje kilka innych typów środowiska wykonawczego systemu Windows do **platformy** przestrzeni nazw. Na przykład **Windows::Foundation —** uchwytu HSTRING reprezentuje ciąg tekstowy Unicode tylko do odczytu, jest mapowany na C + +/ CX `Platform::String` klasy. Po powrocie z operacji środowisko wykonawcze systemu Windows wystąpił błąd HRESULT jest zamapowany na C + +/ CX `Platform::Exception`. Aby uzyskać więcej informacji, zobacz [wbudowanych typów](http://msdn.microsoft.com/en-us/acc196fd-09da-4882-b554-6c94685ec75f).  
  
 C + +/ CX również mapuje niektórych typów w przestrzeniach nazw środowiska wykonawczego systemu Windows w celu zwiększenia funkcjami typu. W przypadku tych typów C + +/ CX zapewnia pomocnika konstruktory i metody, które są specyficzne dla języka C++ i nie są dostępne w pliku winmd standardowa typu.  
  
 Wartość struktury, który obsługuje nowe konstruktory i metody pomocnicze przedstawiono. Jeśli zostały wcześniej zapisane kod, który używa struktury inicjowania list, Zmień, aby użyć nowo dodanego konstruktorów.  
  
 **Windows::Foundation —**  
  
-   punkt  
  
-   Rect  
  
-   Rozmiar  
  
 **Windows::UI**  
  
-   Kolor  
  
 **Windows::UI::XAML**  
  
-   CornerRadius  
  
-   Czas trwania  
  
-   GridLength  
  
-   Grubość  
  
 **Windows::UI::XAML::Interop**  
  
1.  TypeName  
  
 **Windows::UI::XAML::Media**  
  
-   Matrix  
  
 **Windows::UI::XAML::Media::Animation**  
  
-   KeyTime  
  
-   RepeatBehavior  
  
 **Windows::UI::XAML::Media::Media3D**  
  
-   Matrix3D  
  
## <a name="mapping-the-clr-to-ccx"></a>Mapowanie CLR dla C + +/ CX  
 Jeśli Kompilatory języka Visual C++ lub C# do odczytu pliku winmd, automatycznie mapują niektórych typów w pliku metadanych dla odpowiednich C + +/ CX lub CLR typów. Na przykład w środowisku CLR, IVector\<T > jest mapowany interfejsu IList\<T >. Jednak w języku C + +/ CX, IVector\<T > interfejsu nie jest zamapowany do innego typu.  
  
 IReference\<T > w środowisku wykonawczym systemu Windows mapuje Nullable\<T > w .NET.  
  
## <a name="see-also"></a>Zobacz też  
 [Współdziałanie z innymi językami](../cppcx/interoperating-with-other-languages-c-cx.md)