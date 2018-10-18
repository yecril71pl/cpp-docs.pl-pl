---
title: Tworzenie dostawcy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/15/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, creating
ms.assetid: 2506ba8f-010d-4231-aac1-387432f7b6b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0dbdf7350eeba1a29392bafc2f099a857e212e37
ms.sourcegitcommit: db6b2ad3195e71abfb60b62f3f015f08b0a719d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2018
ms.locfileid: "49410749"
---
# <a name="creating-the-provider"></a>Tworzenie dostawcy

## <a name="to-create-an-ole-db-provider-with-the-atl-ole-db-provider-wizard"></a>Aby utworzyć dostawcę OLE DB przy użyciu biblioteki ATL OLE DB Provider Kreatora

1. Kliknij prawym przyciskiem myszy projekt.

1. W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **Dodaj klasę**.

1. W **Dodaj klasę** dialogowego **zainstalowane** > **Visual C++** > **ATL**, wybierz **Dostawcy OLE DB ATL** ikonę, a następnie kliknij przycisk **Otwórz**.

1. W **Kreator biblioteki ATL OLE DB Provider**, podaj krótką nazwę dostawcy w **krótką nazwę** pole. Poniższe tematy użyć krótkiej nazwy "MyProvider", ale możesz użyć innej nazwy. Pozostałe pola nazw wypełnić według nazwy, które można wprowadzić.

1. Edytuj pozostałe pola nazw, jeśli to konieczne. Oprócz obiektowe i plikowe nazwy można edytować następujących czynności:

   - **Klasa coclass**: Nazwa która używa modelu COM w celu utworzenia dostawcy.

   - **Identyfikator progID**: identyfikator programowy, czyli ciąg tekstowy, który można używać zamiast identyfikatora GUID.

   - **Wersja**: używany z ProgID i Coclass do generowania identyfikatora programowe zależne od wersji

1. Kliknij przycisk **Zakończ**.

## <a name="see-also"></a>Zobacz też

[Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)
