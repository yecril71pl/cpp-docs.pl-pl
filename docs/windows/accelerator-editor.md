---
title: Edytor klawiszy skrótów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.accelerator.F1
dev_langs:
- C++
helpviewer_keywords:
- accelerator tables [C++], editing
- tables [Visual Studio], accelerator key
- accelerator keys
- resource editors, Accelerator editor
- keyboard shortcuts [C++], Accelerator editor
- Accelerator editor
ms.assetid: 013c30b6-5d61-4f1c-acef-8bd15bed7060
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: feece642928db70a2b78dd3a4117b695b19f4af9
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39466075"
---
# <a name="accelerator-editor"></a>Edytor klawiszy skrótów
Tabeli klawiszy skrótu jest zasobem Windows, który zawiera listę klawisze skrótów (znany także jako klawisze skrótów) i identyfikatory poleceń, które są skojarzone z nimi. Program może mieć więcej niż jednej tabeli akceleratora.  
  
 Zwykle akceleratorów są używane jako skróty klawiaturowe dla poleceń programu, które są również dostępne w menu lub paska narzędzi. Jednak można użyć tabeli akceleratora do definiowania kombinacji klawiszy dla polecenia, które nie mają skojarzonych z nimi obiektu interfejsu użytkownika.  
  
 Możesz użyć [Widok klas](http://msdn.microsoft.com/8d7430a9-3e33-454c-a9e1-a85e3d2db925) można dołączyć klucza polecenia klawiszy skrótów do kodu.  
  
 Edytor klawiszy skrótów można:  
  
-   [Ustawianie właściwości klawiszy skrótów](../windows/setting-accelerator-properties.md)  
  
-   [Kojarzenie klawisza skrótu z elementem Menu](../windows/associating-an-accelerator-key-with-a-menu-item.md)  
  
-   [Edytowanie tabel akceleratora](../windows/editing-accelerator-tables.md)  
  
-   [Użyj wstępnie zdefiniowane klawisze skrótów](../windows/predefined-accelerator-keys.md)  
  
    > [!TIP]
    >  Podczas korzystania z Edytor klawiszy skrótów, można kliknąć prawym przyciskiem myszy, aby wyświetlić menu skrótów z najczęściej używanymi poleceniami. Dostępne polecenia zależą od tego, wskaźnik wskazuje na.  
  
    > [!NOTE]
    >  Windows nie pozwalają na tworzenie tabel akceleratora puste. Jeśli utworzenia tabeli akceleratora żadnych wpisów, zostanie usunięta automatycznie po zapisaniu tabeli.  
  
 Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework.* Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Edytory zasobów](../windows/resource-editors.md)