---
title: "Edytor klawiszy skrótów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.accelerator.F1
dev_langs: C++
helpviewer_keywords:
- accelerator tables [C++], editing
- tables [Visual Studio], accelerator key
- accelerator keys
- resource editors, Accelerator editor
- keyboard shortcuts [C++], Accelerator editor
- Accelerator editor
ms.assetid: 013c30b6-5d61-4f1c-acef-8bd15bed7060
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e078dbd3dc8d462ef4bca6e6f1056afb9ce8724c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="accelerator-editor"></a>Edytor klawiszy skrótów
Tabela akceleratora jest zasób systemu Windows, który zawiera listę klawisze skrótów (znanej także jako klawisze skrótu) i identyfikatory poleceń, które są skojarzone z nimi. Program może mieć więcej niż jednej tabeli akceleratora.  
  
 Zwykle akceleratorów są używane jako skróty klawiaturowe dla poleceń programu, które są również dostępne w menu lub pasek narzędzi. Jednak można użyć tabeli akceleratora do definiowania kombinacje klawiszy poleceń, które nie mają obiektu interfejsu użytkownika, skojarzone z nimi.  
  
 Można użyć [widoku klasy](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925) na połączeniu klucza poleceń klawiszy skrótów do kodu.  
  
 Edytor klawiszy skrótów można:  
  
-   [Ustawianie właściwości klawiszy skrótów](../windows/setting-accelerator-properties.md)  
  
-   [Kojarzenie klawisza skrótu z elementu Menu.](../windows/associating-an-accelerator-key-with-a-menu-item.md)  
  
-   [Edytowanie tabel akceleratora](../windows/editing-accelerator-tables.md)  
  
-   [Użyj wstępnie zdefiniowane klawisze skrótów](../windows/predefined-accelerator-keys.md)  
  
    > [!TIP]
    >  Podczas używania Edytor klawiszy skrótów, należy kliknąć prawym przyciskiem myszy, aby wyświetlić menu skrótów często używanych poleceń. Dostępne polecenia zależą od tego, co wskaźnik wskazuje.  
  
    > [!NOTE]
    >  System Windows nie zezwala na tworzenie tabel akceleratora puste. Po utworzeniu tabeli akceleratora z żadnych wpisów jest usuwane automatycznie podczas zapisywania tabeli.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Edytory zasobów](../windows/resource-editors.md)

