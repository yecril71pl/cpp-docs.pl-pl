---
title: Tworzenie kontenera kontrolek ActiveX MFC
ms.date: 09/12/2018
f1_keywords:
- vc.appwiz.activex.container
helpviewer_keywords:
- MFC ActiveX controls [MFC], containers
- ActiveX control containers [MFC], creating
- containers [MFC], creating
- OLE controls [MFC], containers
ms.assetid: ec70e137-7c14-4940-bd0e-fd4edcc63ea5
ms.openlocfilehash: 27f229a23595d4842a77409a3cedc7a57aa43e6c
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079435"
---
# <a name="creating-an-mfc-activex-control-container"></a>Tworzenie kontenera kontrolek ActiveX MFC

Kontener formantów ActiveX jest programem nadrzędnym, który dostarcza środowisko do uruchamiania kontrolki ActiveX (dawniej OLE). Można utworzyć aplikację, która może zawierać kontrolki ActiveX z MFC lub bez, ale jest to znacznie łatwiejsze w przypadku MFC.

>[!IMPORTANT]
> Kontrolka ActiveX to Starsza technologia, która nie powinna być używana do nowych celów programistycznych. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [kontrolki ActiveX](../activex-controls.md).

Tworzenie programu kontenera MFC przy użyciu [Kreatora aplikacji MFC](../../mfc/reference/mfc-application-wizard.md) pozwala uzyskać dostęp do wielu funkcji formantów ActiveX i automatyzacji, które są implementowane przez klasy MFC i ActiveX. Te funkcje obejmują edycję wizualizacji, automatyzację, tworzenie plików złożonych i obsługę formantów. Opcje edycji wizualnej Kreatora aplikacji MFC, które będą obsługiwane przez program nadrzędny, obejmują tworzenie kontenera, mini serwer, pełny serwer i program, który jest zarówno kontenerem, jak i serwerem.

- **Nowa aplikacja MFC**. Aby utworzyć nowy program MFC, który obejmuje automatyzację, edycję wizualizacji, pliki złożone lub obsługę kontroli, użyj Kreatora aplikacji MFC i wybierz odpowiednie opcje automatyzacji.

- **Istniejąca aplikacja MFC**. Jeśli dodajesz kontrolkę zawieranie do istniejącej aplikacji MFC, zobacz [kontenery kontrolek OLE: ręczne włączanie zawierania kontrolek OLE](../../mfc/activex-control-containers-manually-enabling-activex-control-containment.md).

### <a name="to-create-an-activex-container-for-any-of-the-following-types-of-applications"></a>Aby utworzyć kontener ActiveX dla dowolnego z następujących typów aplikacji

1. [Kontenery](../../mfc/containers.md)

1. [Edytowanie wizualizacji](../../mfc/ole-mfc.md)

1. [Kontrolki ActiveX MFC](../../mfc/mfc-activex-controls.md)

## <a name="see-also"></a>Zobacz też

[C++typy projektów w programie Visual Studio](../../build/reference/visual-cpp-project-types.md)
