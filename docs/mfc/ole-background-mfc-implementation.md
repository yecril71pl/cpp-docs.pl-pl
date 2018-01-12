---
title: 'Podstawy OLE: Implementacja MFC | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IMarshall
- IMoniker
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 530cc14135fd38e2177e00dc87974e96ffe24b6c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ole-background-mfc-implementation"></a>Podstawy OLE: implementacja MFC
Ze względu na rozmiar i złożoność raw OLE interfejsu API wywoływania go bezpośrednio do pisania aplikacji OLE może być bardzo czasochłonne. Celem wdrożenia Microsoft Foundation Class Library OLE jest aby zmniejszyć ilość pracy, które musisz wykonać do pisania aplikacji obsługujących OLE, kompletne.  
  
 W tym artykule opisano części OLE interfejsu API, które nie zostały wdrożone w MFC. Dyskusja wyjaśniono również sposób mapowania co to jest zaimplementowana OLE część zestawu Windows SDK.  
  
##  <a name="_core_portions_of_ole_not_implemented_by_the_class_library"></a>Części OLE nie jest zaimplementowana przez biblioteki klas  
 Kilka interfejsów i funkcje OLE nie są bezpośrednio dostarczane przez MFC. Jeśli chcesz korzystać z tych funkcji, OLE interfejsu API można wywołać bezpośrednio.  
  
 Imoniker — interfejs  
 `IMoniker` Interfejs jest implementowany przez biblioteki klas (na przykład `COleServerItem` klasy), ale nie został wcześniej widoczne dla programisty. Aby uzyskać więcej informacji na temat tego interfejsu Zobacz OLE Moniker implementacje OLE część zestawu Windows SDK. Jednakże, zobacz też klasy [CMonikerFile](../mfc/reference/cmonikerfile-class.md) i [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md).  
  
 Interfejsy IMarshal i IUnknown  
 **IUnknown** interfejs jest implementowany przez biblioteki klas, ale nie jest widoczna dla programisty. **IMarshal** interfejs nie jest implementowana przez biblioteki klas, ale jest używana wewnętrznie. Serwery automatyzacji utworzony za pomocą biblioteki klas już mieć organizowanie wbudowane możliwości.  
  
 OLE (pliki złożone)  
 Pliki złożone częściowo są obsługiwane przez biblioteki klas. Żadna funkcji, które bezpośrednio manipulowania pliki złożone poza tworzenia nie jest obsługiwana. MFC używa klasy **COleFileStream** do obsługi manipulowania strumieni z funkcji standardowego pliku. Aby uzyskać więcej informacji, zobacz artykuł [kontenery: pliki złożone](../mfc/containers-compound-files.md).  
  
 W trakcie serwerów i obsługi obiektu  
 W trakcie serwerów i obsługi obiektu umożliwiają implementacji visual edycji danych lub pełne obiektów składnik modelu COM. w biblioteki dołączanej (dynamicznie DLL). Aby to zrobić, można zaimplementować biblioteki DLL przez bezpośrednie wywoływanie OLE interfejsu API. Jednak jeśli piszesz serwera automatyzacji i serwer nie ma interfejsu użytkownika, można użyć kreatorami AppWizard serwera server wewnątrzprocesowe i umieszcza je w pełni do biblioteki DLL. Aby uzyskać więcej informacji o tych tematów, zobacz [serwery automatyzacji](../mfc/automation-servers.md).  
  
> [!TIP]
>  Najprostszym sposobem wdrożenia serwera automatyzacji jest umieszczony w bibliotece DLL. MFC obsługuje tej metody.  
  
 Aby uzyskać więcej informacji dotyczących sposobu klasy Microsoft Foundation OLE implementować interfejsów OLE, zobacz Uwagi techniczne MFC [38](../mfc/tn038-mfc-ole-iunknown-implementation.md), [39](../mfc/tn039-mfc-ole-automation-implementation.md), i [40](../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawy OLE](../mfc/ole-background.md)   
 [Podstawy OLE: strategie implementacji](../mfc/ole-background-implementation-strategies.md)

