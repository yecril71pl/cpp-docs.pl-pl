---
title: Edytor ciągów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.string.F1
dev_langs:
- C++
helpviewer_keywords:
- String editor
- string tables
- string tables, String editor
- string editing
- string editing, string tables
- resource editors, String editor
- strings [C++], editing
ms.assetid: f71ab8de-3068-4e29-8e28-5a33d18dd416
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 23211293313135cb0341ac234014ae3c144b7fec
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891379"
---
# <a name="string-editor"></a>Edytor ciągów znaków
Tabela ciągów jest zasób systemu Windows, który zawiera listę identyfikatorów, wartości oraz podpisów dla wszystkich ciągów aplikacji. Na przykład monity pasek stanu znajdują się w tabeli ciągów.  
  
 Podczas tworzenia aplikacji, może mieć kilka tabele ciągów — po jednej dla każdego języka lub warunku. Jednak wykonywalnego modułu jest tylko jedna tabela ciągów. Uruchomionej aplikacji można odwołania kilku tabel ciągów, jeśli umieścić tabelami w różnych biblioteki dll.  
  
 Tabele ciągów ułatwiają do zlokalizowania aplikacji w różnych językach. W przypadku wszystkich ciągów w tabeli ciągów, można lokalizować przez tłumaczenie ciągi (i innych zasobów) bez zmieniania kodu źródłowego aplikacji. Jest to zazwyczaj bardziej pożądane niż ręcznie Znajdowanie i zastępowanie różne ciągi w plikach źródłowych.  
  
 Za pomocą edytora ciągów, można:  
  
-   [Wyszukaj jeden lub więcej ciągów](../windows/finding-a-string.md).  
  
-   Szybko [Wstaw nowe wpisy](../windows/adding-or-deleting-a-string.md) w tablicy ciągów.  
  
-   [Przenoszenie ciągu z jednego pliku zasobu do innej](../windows/moving-a-string-from-one-resource-file-to-another.md)  
  
-   [Użyj edycji w miejscu dla właściwości Identyfikatora, wartość i podpis](../windows/changing-the-properties-of-a-string.md) i natychmiast zobaczyć zmiany.  
  
-   [Zmiana właściwości podpisu wielu ciągów](../windows/changing-the-caption-property-of-multiple-strings.md)  
  
-   [Dodaj do ciągu znaków specjalnych ani formatowania](../windows/adding-formatting-or-special-characters-to-a-string.md)  
  
    > [!NOTE]
    >  Windows pozwala na tworzenie tabel pusty ciąg. Po utworzeniu tabeli ciągów z żadnych wpisów jest usuwane automatycznie podczas zapisywania pliku zasobu.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych (te, których miejscem docelowym jest środowisko uruchomieniowe języka wspólnego), zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [wskazówki: Lokalizowanie formularzy systemu Windows](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5) i [Wskazówki: Korzystanie z zasobów dla lokalizacji ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Edytory zasobów](../windows/resource-editors.md)   
 [Ciągi](http://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)   
 [Ciągi-informacje](http://msdn.microsoft.com/library/windows/desktop/ms647465.aspx)

