---
title: Edytor ciągów znaków (C++) | Dokumentacja firmy Microsoft
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
- string tables [C++], String editor
- string editing
- string editing, string tables
- resource editors [C++], String editor
- strings [C++], editing
ms.assetid: f71ab8de-3068-4e29-8e28-5a33d18dd416
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 02248c7c6f61823649d9643a7321677e23a4afbf
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382911"
---
# <a name="string-editor-c"></a>Edytor ciągów znaków (C++)

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

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, (te, których platformą docelową środowiska uruchomieniowego języka wspólnego), zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Instruktaż: Lokalizowanie interfejsów Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3\(v=vs.100\)).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytory zasobów](../windows/resource-editors.md)<br/>
[Ciągi](https://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)<br/>
[Ciągi — informacje](/windows/desktop/menurc/about-strings)

