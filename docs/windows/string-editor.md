---
title: Edytor ciągów znaków | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 51470a572ec9540f203bb4cff80981fe6ad15dd1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42578574"
---
# <a name="string-editor"></a>Edytor ciągów znaków

Tabela ciągów jest zasobem Windows, który zawiera listę identyfikatorów, wartości i podpisy dla wszystkich ciągów aplikacji. Na przykład monity pasek stanu znajdują się w tabeli ciągów.

Podczas tworzenia aplikacji, może mieć kilka tabel ciągów — jeden dla każdego języka lub warunku. Jednak modułowi wykonywalnemu ma tylko jedną tabelę ciągów. Uruchomionej aplikacji można odwoływać kilka tabel ciągów, jeżeli umieścisz tabel do różnych bibliotek DLL.

Tabele ciągów należy ułatwia lokalizowanie aplikacji w różnych językach. Jeśli wszystkie ciągi znajdują się w tabeli ciągów, można lokalizować aplikacji dzięki translacji ciągi (i inne zasoby) bez konieczności zmieniania kodu źródłowego. Jest to zazwyczaj bardziej pożądane niż ręcznie Znajdowanie i zastępowanie różnych ciągów w plikach źródłowych.

Za pomocą edytora ciągów, możesz wykonywać następujące czynności:

- [Wyszukaj jeden lub więcej ciągów](../windows/finding-a-string.md).

- Szybko [Wstaw nowe wpisy](../windows/adding-or-deleting-a-string.md) w tablicy ciągów.

- [Przenoszenie ciągu z jednego pliku zasobu do innego](../windows/moving-a-string-from-one-resource-file-to-another.md)

- [Użyj edycji w miejscu dla właściwości Identyfikatora, wartości i podpis](../windows/changing-the-properties-of-a-string.md) i natychmiast wyświetlić zmiany.

- [Zmiana właściwości podpisu lub wielu ciągów](../windows/changing-the-caption-property-of-multiple-strings.md)

- [Dodaj znaków specjalnych ani formatowania na ciąg](../windows/adding-formatting-or-special-characters-to-a-string.md)

   > [!NOTE]
   > Windows nie zezwala na tworzenie tabel pusty ciąg. Jeśli utworzysz tabeli ciągów z żadnych wpisów, zostanie usunięta automatycznie podczas zapisywania pliku zasobów.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, (te, których platformą docelową środowiska uruchomieniowego języka wspólnego), zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Instruktaż: Lokalizowanie interfejsów Windows Forms](http://msdn.microsoft.com/9a96220d-a19b-4de0-9f48-01e5d82679e5) i [Wskazówki: Korzystanie z zasobów for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytory zasobów](../windows/resource-editors.md)  
[Ciągi](http://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)  
[Ciągi — informacje](/windows/desktop/menurc/about-strings)

