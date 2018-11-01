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
ms.openlocfilehash: 6372f28c78be99af9e329ff83ef531d18ad2480f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476677"
---
# <a name="ole-background-mfc-implementation"></a>Podstawy OLE: implementacja MFC

Ze względu na rozmiar i złożoność pierwotne OLE interfejsu API wywołując ją bezpośrednio do pisania aplikacji OLE może być bardzo czasochłonne. Celem wdrożenia bibliotekę Microsoft Foundation Class OLE jest aby zmniejszyć ilość pracy, który trzeba napisać obsługą OLE, w pełni funkcjonalne aplikacje.

W tym artykule opisano części OLE interfejsu API, które nie zostały wdrożone w MFC. Omówienie wyjaśniono również, jak co to jest implementowany mapuje OLE część zestawu Windows SDK.

##  <a name="_core_portions_of_ole_not_implemented_by_the_class_library"></a> Fragmenty nie jest zaimplementowana przez bibliotekę klasy OLE

Kilka interfejsów i funkcje OLE nie są bezpośrednio oferowane przez MFC. Jeśli chcesz korzystać z tych funkcji, możesz bezpośrednio wywołać OLE interfejsu API.

Imoniker — interfejs `IMoniker` interfejs jest implementowany przez bibliotekę klas (na przykład `COleServerItem` klasy), ale nie została wcześniej narażony na potwierdzeniu programisty. Aby uzyskać więcej informacji na temat tego interfejsu Zobacz OLE Moniker implementacji w sekcji OLE zestawu Windows SDK. Jednak również zobaczyć klasy [CMonikerFile](../mfc/reference/cmonikerfile-class.md) i [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md).

IUnknown i interfejsy IMarshal `IUnknown` interfejs jest implementowany przez bibliotekę klas, ale nie jest narażony na potwierdzeniu programisty. `IMarshal` Interfejsu nie jest zaimplementowana przez bibliotekę klas, ale jest używana wewnętrznie. Serwery automatyzacji utworzone przy użyciu biblioteki klas już mieć marshaling funkcji wbudowanych.

Plików złożonych OLE (pliki złożone) są obsługiwane częściowo przez bibliotekę klas. Żadna z funkcji, które bezpośrednio modyfikować pliki złożone poza tworzenia nie jest obsługiwana. MFC używa klasy `COleFileStream` umożliwiają manipulowanie strumieni przy użyciu standardowych plikowych funkcji. Aby uzyskać więcej informacji, zobacz artykuł [kontenery: pliki złożone](../mfc/containers-compound-files.md).

Serwery wewnątrzprocesowe serwerów w procesie i obsługi obiektu i obiekt obsługi umożliwiają wdrażania visual edycji danych lub pełne obiektów Component Object Model (COM) w bibliotece dołączanej (dynamicznie DLL). Aby to zrobić, można zaimplementować biblioteki DLL przez OLE bezpośredniego wywoływania interfejsu API. Jednak jeśli piszesz serwera automatyzacji, a serwer nie ma interfejsu użytkownika, można użyć przez kreatora AppWizard w celu podejmowania serwera wewnątrz procesowego i umieść je całkowicie biblioteki DLL. Aby uzyskać więcej informacji na temat tych tematów, zobacz [serwerów automatyzacji](../mfc/automation-servers.md).

> [!TIP]
>  Najprostszym sposobem wdrożenia serwera usługi Automation jest umieścić go w bibliotece DLL. Biblioteka MFC obsługuje takie podejście.

Aby uzyskać więcej informacji na temat sposobu klas Microsoft Foundation OLE implementacji interfejsów OLE, zobacz Uwagi techniczne dotyczące MFC [38](../mfc/tn038-mfc-ole-iunknown-implementation.md), [39](../mfc/tn039-mfc-ole-automation-implementation.md), i [40](../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md).

## <a name="see-also"></a>Zobacz też

[Podstawy OLE](../mfc/ole-background.md)<br/>
[Podstawy OLE: strategie implementacji](../mfc/ole-background-implementation-strategies.md)

