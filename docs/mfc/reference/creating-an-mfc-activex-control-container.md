---
title: Tworzenie kontenera kontrolek ActiveX MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.activex.container
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], containers
- ActiveX control containers [MFC], creating
- containers [MFC], creating
- OLE controls [MFC], containers
ms.assetid: ec70e137-7c14-4940-bd0e-fd4edcc63ea5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7167f00e3abf74d4638bc79615d68ed81fafabf9
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45535122"
---
# <a name="creating-an-mfc-activex-control-container"></a>Tworzenie kontenera kontrolek ActiveX MFC
Kontener formantu ActiveX jest programu nadrzędnego, który dostarcza środowisko dla formantu ActiveX (dawniej OLE) uruchomić. Można utworzyć aplikację może zawierać kontrolki ActiveX z lub bez MFC, ale jest znacznie łatwiejsze wykonać za pomocą MFC.

>[!IMPORTANT]
> ActiveX jest technologią starszą, która nie powinny być używane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji na temat nowych technologii, które wypierają ActiveX zobacz [formantów ActiveX](../activex-controls.md).  
  
 Tworzenie MFC kontenera programu za pomocą [Kreator aplikacji MFC](../../mfc/reference/mfc-application-wizard.md) umożliwia dostęp do funkcji wielu formantów ActiveX i automatyzacji, które są implementowane przez klasy MFC i ActiveX. Te funkcje obejmują edycja wizualna, Automation, tworzenie złożonych plików oraz obsługę formantów. Kreator aplikacji MFC visual edycji obsługujących program nadrzędnego dostępne są następujące opcje tworzenia kontenera, mini serwer, pełny serwer i program, który zarówno kontenera, jak i serwera.  
  
-   **Nowa aplikacja MFC**. Aby utworzyć nowy program MFC, która obejmuje usługi Automation, edycja wizualna złożone pliki, lub kontrolować pomocy technicznej, użyj Kreatora aplikacji MFC i wybierz odpowiednie opcje automatyzacji.  
  
-   **Istniejącej aplikacji MFC**. Jeśli dodajesz zawieranie kontrolek do istniejącej aplikacji MFC, zobacz [kontenery OLE kontrolek: ręczne Włączanie OLE zawieranie kontrolek](../../mfc/activex-control-containers-manually-enabling-activex-control-containment.md).  
  
### <a name="to-create-an-activex-container-for-any-of-the-following-types-of-applications"></a>Aby utworzyć kontener ActiveX dla żadnego z następujących typów aplikacji  
  
1.  [Kontenery](../../mfc/containers.md)  
  
2.  [Edycja wizualna](../../mfc/ole-mfc.md)  
  
3.  [Kontrolki MFC ActiveX](../../mfc/mfc-activex-controls.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Typy projektów Visual C++](../../ide/visual-cpp-project-types.md)

