---
title: 'Podstawy OLE: implementacja MFC'
ms.date: 11/04/2016
f1_keywords:
- IMarshall
- IMoniker
helpviewer_keywords:
- MFC libraries, implementing
- OLE MFC library implementation
- OLE IMarshal interface
- IMoniker interface, MFC
- IMarshall class [MFC]
- OLE, compound files
- OLE IMoniker interface
- OLE IUnknown
ms.assetid: 2b67016a-d78e-4d60-925f-c28ec8fb6180
ms.openlocfilehash: 1dffdafbd02697db5aec341fec253c84217a0faf
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619877"
---
# <a name="ole-background-mfc-implementation"></a>Podstawy OLE: implementacja MFC

Ze względu na rozmiar i złożoność surowego interfejsu API OLE, wywołanie go bezpośrednio do pisania aplikacji OLE może być bardzo czasochłonne. Celem biblioteka MFC implementacji OLE jest zredukowanie nakładu pracy, które należy wykonać, aby napisać w pełni funkcjonalne aplikacje obsługujące technologię OLE.

W tym artykule wyjaśniono części interfejsu API OLE, które nie zostały zaimplementowane wewnątrz MFC. W omówieniu wyjaśniono również, jak zaimplementowane są mapy do sekcji OLE Windows SDK.

## <a name="portions-of-ole-not-implemented-by-the-class-library"></a><a name="_core_portions_of_ole_not_implemented_by_the_class_library"></a>Fragmenty OLE niezaimplementowane przez bibliotekę klas

Niektóre interfejsy i funkcje OLE nie są bezpośrednio udostępniane przez MFC. Jeśli chcesz korzystać z tych funkcji, możesz wywołać interfejs API OLE bezpośrednio.

Interfejs IMoniker — Interfejs `IMoniker` jest implementowany przez bibliotekę klas (na przykład `COleServerItem` Klasa), ale nie był wcześniej narażony na programistę. Aby uzyskać więcej informacji na temat tego interfejsu, zobacz Implementacja monikera OLE w sekcji OLE Windows SDK. Jednak Zobacz też klasy [CMonikerFile](reference/cmonikerfile-class.md) i [CAsyncMonikerFile](reference/casyncmonikerfile-class.md).

Interfejsy IUnknown i IMarshal `IUnknown` interfejs jest implementowany przez bibliotekę klas, ale nie jest narażony na programistę. `IMarshal`Interfejs nie jest zaimplementowany przez bibliotekę klas, ale jest używany wewnętrznie. Serwery automatyzacji skompilowane przy użyciu biblioteki klas już mają wbudowane funkcje organizowania.

Pliki złożone DOCFILES (pliki złożone) są częściowo obsługiwane przez bibliotekę klas. Żadna z funkcji, które nie manipulują plikami złożonymi Poza tworzeniem, nie jest obsługiwana. MFC używa klasy `COleFileStream` do obsługi manipulowania strumieniami przy użyciu standardowych funkcji plików. Aby uzyskać więcej informacji, zobacz [kontenery artykułów: pliki złożone](containers-compound-files.md).

Serwery wewnątrzprocesowe i programy obsługi obiektów w procesie i programy obsługi obiektów, które umożliwiają implementację danych edycji wizualizacji lub pełnych obiektów Component Object Model (COM) w bibliotece dołączanej dynamicznie (DLL). W tym celu można zaimplementować bibliotekę DLL przez bezpośrednie wywołanie interfejsu API OLE. Jeśli jednak piszesz serwer automatyzacji, a serwer nie ma interfejsu użytkownika, możesz użyć AppWizard, aby serwer na serwerze i umieścić go w całości w bibliotece DLL. Aby uzyskać więcej informacji o tych tematach, zobacz [serwery automatyzacji](automation-servers.md).

> [!TIP]
> Najprostszym sposobem implementacji serwera automatyzacji jest umieszczenie go w bibliotece DLL. MFC obsługuje to podejście.

Aby uzyskać więcej informacji na temat sposobu implementacji interfejsów OLE przez klasy Microsoft Foundation OLE, zobacz informacje techniczne dotyczące MFC [38](tn038-mfc-ole-iunknown-implementation.md), [39](tn039-mfc-ole-automation-implementation.md)i [40](tn040-mfc-ole-in-place-resizing-and-zooming.md).

## <a name="see-also"></a>Zobacz też

[Podstawy OLE](ole-background.md)<br/>
[Podstawy OLE: strategie implementacji](ole-background-implementation-strategies.md)
