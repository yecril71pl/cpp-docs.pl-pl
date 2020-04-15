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
ms.openlocfilehash: 25c98c3683a8656bb5188f22d0464d25a4901f49
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364529"
---
# <a name="ole-background-mfc-implementation"></a>Podstawy OLE: implementacja MFC

Ze względu na rozmiar i złożoność surowego interfejsu API OLE wywołanie go bezpośrednio do zapisu aplikacji OLE może być bardzo czasochłonne. Celem implementacji biblioteki klas Microsoft Foundation ole jest zmniejszenie ilości pracy, którą należy wykonać, aby napisać w pełni funkcjonalne aplikacje obsługujące ole.

W tym artykule opisano części interfejsu API OLE, które nie zostały zaimplementowane wewnątrz MFC. W dyskusji wyjaśniono również, jak zaimplementowano mapy do sekcji OLE w usłudze Windows SDK.

## <a name="portions-of-ole-not-implemented-by-the-class-library"></a><a name="_core_portions_of_ole_not_implemented_by_the_class_library"></a>Fragmenty OLE nie zaimplementowane przez bibliotekę klas

Kilka interfejsów i funkcji OLE nie są bezpośrednio dostarczane przez MFC. Jeśli chcesz korzystać z tych funkcji, można wywołać ole interfejsu API bezpośrednio.

Interfejs IMoniker `IMoniker` Interfejs jest implementowany przez bibliotekę `COleServerItem` klas (na przykład klasę), ale nie był wcześniej narażony na programatora. Aby uzyskać więcej informacji na temat tego interfejsu, zobacz Implementacje ole moniker w sekcji OLE w windows SDK. Jednak zobacz także klasę [CMonikerFile](../mfc/reference/cmonikerfile-class.md) i [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md).

Interfejsy IUnknown i IMarshal `IUnknown` Interfejs jest implementowany przez bibliotekę klas, ale nie jest narażony na programatora. Interfejs `IMarshal` nie jest implementowany przez bibliotekę klas, ale jest używany wewnętrznie. Serwery automatyzacji utworzone przy użyciu biblioteki klas mają już wbudowane możliwości organizowania.

Pliki docfiles (Compound Files) Złożone pliki są częściowo obsługiwane przez bibliotekę klas. Żadna z funkcji, które bezpośrednio manipulować złożonych plików poza tworzenie są obsługiwane. MFC używa `COleFileStream` klasy do obsługi manipulowania strumieniami ze standardowymi funkcjami plików. Aby uzyskać więcej informacji, zobacz artykuł [Kontenery: Pliki złożone](../mfc/containers-compound-files.md).

Serwery w trakcie i programy obsługi obiektów W trakcie serwerów i programów obsługi obiektów umożliwiają implementację wizualnej edycji danych lub obiektów COM (full Component Object Model) w bibliotece łącza dynamicznego (DLL). Aby to zrobić, można zaimplementować bibliotekę DLL, wywołując bezpośrednio interfejsu API OLE. Jeśli jednak piszesz serwer automatyzacji, a serwer nie ma interfejsu użytkownika, możesz użyć AppWizard, aby serwer stał się serwerem w trakcie procesu i całkowicie przekształcić go w bibliotekę DLL. Aby uzyskać więcej informacji na temat tych tematów, zobacz [Serwery automatyzacji](../mfc/automation-servers.md).

> [!TIP]
> Najprostszym sposobem zaimplementowania serwera automatyzacji jest umieszczenie go w biblioteki DLL. MFC obsługuje to podejście.

Aby uzyskać więcej informacji na temat sposobu implementowania interfejsów OLE przez klasy OLE w programie Microsoft Foundation, zobacz Uwagi techniczne MFC [38](../mfc/tn038-mfc-ole-iunknown-implementation.md), [39](../mfc/tn039-mfc-ole-automation-implementation.md)i [40](../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md).

## <a name="see-also"></a>Zobacz też

[Podstawy OLE](../mfc/ole-background.md)<br/>
[Podstawy OLE: strategie implementacji](../mfc/ole-background-implementation-strategies.md)
