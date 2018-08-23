---
title: Przypisywanie klawiszy skrótów do poleceń Menu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- access keys [C++], checking
- menus, shortcut keys
- keyboard shortcuts [C++], command assignments
- access keys [C++], assigning
- mnemonics, adding to menus
- keyboard shortcuts [C++], uniqueness checking
- mnemonics, uniqueness checking
- Check Mnemonics command
ms.assetid: fbcf1a00-af6a-4171-805a-0ac01d4e8b0d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ab8ebb204b30883894e04c5d5d8a90f12c63a29b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591471"
---
# <a name="assigning-access-keys-to-menu-commands"></a>Przypisywanie klawiszy skrótów do poleceń menu

Klucz dostępu (Mnemonik, który umożliwia użytkownikowi wybranie w menu za pomocą klawiatury) można przypisać do menu i poleceń menu.

### <a name="to-assign-an-access-shortcut-key-to-a-menu-command"></a>Aby przypisać klawisza dostępu (skrót) do polecenia menu

1. Wpisz znak (`&`) przed litery w nazwie menu lub nazwa polecenia, aby określić tę literę jako odpowiedniego klucza dostępu. Na przykład "& plik" ustawia **Alt**+**F** jako klawisza skrótu dla **pliku** menu w aplikacji napisanych dla Microsoft Windows.

   Element menu będzie udostępniać widoczne oznaką jedna z liter ma do niej przypisany klawisz skrótu. Następujące list, zostaną wyświetlone handlowe "i" podkreślone (warunkowe w systemie operacyjnym).

   > [!NOTE]
   > Upewnij się, wszystkie klucze dostępu w menu są unikatowe, klikając prawym przyciskiem myszy menu i wybierając pozycję **Sprawdź mnemonik** z menu skrótów.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytor menu](../windows/menu-editor.md)