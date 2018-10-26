---
title: Edytowanie ciągu w zasobach informacji o wersji (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.version
dev_langs:
- C++
helpviewer_keywords:
- version information resources [C++]
- resources [C++], editing version information
ms.assetid: d3a7d4e4-7d31-47c2-902c-f50b8404ba4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5a456c745a11fa4250ad731f00556b211ad21b8f
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50061706"
---
# <a name="editing-a-string-in-a-version-information-resource-c"></a>Edytowanie ciągu w zasobach informacji o wersji (C++)

### <a name="to-edit-a-string-in-a-version-information-resource"></a>Edytowanie ciągu w zasobach informacji o wersji

1. Kliknij element, jeden raz, następnie ponownie wybierz go, aby rozpocząć jego edycji. Wprowadź zmiany bezpośrednio w **informacje o wersji** tabeli lub [okno właściwości](/visualstudio/ide/reference/properties-window). Wprowadzone zmiany zostaną odzwierciedlone w obu miejscach.

   > [!NOTE]
   > Podczas edytowania `FILEFLAGS` w **informacje o wersji** edytora, zauważysz, nie można ustawić **debugowania**, **kompilacja prywatna**, lub **specjalne Tworzenie** właściwości (w **właściwości** okna) plików .rc:

   - **Informacje o wersji** zestawy edytora **debugowania** właściwość o `#ifdef` w skrypcie zasobów na podstawie `_DEBUG` kompilacji flagi.

   - Jeśli `Private Build` kluczu **wartość** w **informacje o wersji** tabeli, odpowiedni **kompilacja prywatna** właściwości (w **właściwości**  okna) dla `FILEFLAGS` klucz będzie **True**. Jeśli **wartość** jest pusta, właściwość będzie **False**. Podobnie **kompilacji specjalnych** klucza (w **informacje o wersji** tabeli) jest powiązana z **kompilacji specjalnych** właściwość `FILEFLAGS` klucza.

Sekwencja informacji blok ciągu można sortować, klikając nagłówki kolumn wartość lub klucz. Te nagłówki automatyczne rozmieszczanie informacji w wybranej sekwencji.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytor informacji o wersji](../windows/version-information-editor.md)<br/>
[Informacje o wersji (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)