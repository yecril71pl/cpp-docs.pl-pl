---
title: Tworzenie dostawcy | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, creating
ms.assetid: 2506ba8f-010d-4231-aac1-387432f7b6b9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5521215560c84c19f7b661f0c9662752374b68e4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="creating-the-provider"></a>Tworzenie dostawcy
#### <a name="to-create-an-ole-db-provider-with-the-atl-ole-db-provider-wizard"></a>Aby utworzyć dostawcę OLE DB za pomocą OLE DB Provider Kreator ATL  
  
1.  Kliknij prawym przyciskiem myszy projekt.  
  
2.  W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **Dodaj klasę**.  
  
3.  W **Dodaj klasę** okno dialogowe, wybierz opcję **ATL dostawcy OLE DB** ikonę, a następnie kliknij przycisk **Otwórz**.  
  
4.  W OLE DB Provider Kreator ATL, wpisz krótką nazwę dostawcy w **krótką nazwę** pole. Poniższe tematy używać krótką nazwę "MyProvider", ale możesz użyć innej nazwy. Wypełnia pozostałe pola nazw zgodnie z wprowadzona nazwa.  
  
5.  Edytuj pozostałe pola nazw, jeśli to konieczne. Oprócz nazwy obiektu i plik można edytować następujących czynności:  
  
    -   **Coclass**: nazwę, która używa modelu COM w celu utworzenia dostawcy.  
  
    -   **ProgID**: identyfikator programowy, czyli ciąg tekstowy, który może służyć zamiast identyfikatora GUID.  
  
    -   **Wersja**: używane z ProgID i coclass wygenerować identyfikator programowy zależnym od wersji  
  
6.  Kliknij przycisk **Zakończ**.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)