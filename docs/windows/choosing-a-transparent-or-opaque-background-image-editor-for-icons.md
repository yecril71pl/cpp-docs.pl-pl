---
title: Wybieranie tła przezroczystego lub nieprzezroczystego (edytor obrazów dla ikon) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- opaque backgrounds [C++]
- colors [C++], image
- Image editor [C++], transparent or opague backgrounds
- images [C++], transparency
- images [C++], opaque background
ms.assetid: 61b743d9-c86b-405d-9a81-0806431b4363
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 77d9647fd4432bf2ab0cf9e4add2a08ce964b85a
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060081"
---
# <a name="choosing-a-transparent-or-opaque-background-image-editor-for-icons"></a>Wybieranie tła przezroczystego lub nieprzezroczystego (Edytor obrazów dla ikon)

Podczas przenoszenia lub skopiowane z obrazu wszystkie piksele w zaznaczeniu, które odpowiadają bieżącym kolorem tła, są domyślnie przezroczysty; nie ograniczają pikseli w lokalizacji docelowej.

Możesz przełączyć się z przezroczystym tłem (ustawienie domyślne) tło nieprzezroczyste i z powrotem. Korzystając z narzędzia zaznaczania **przezroczyste tło** i **tło nieprzezroczyste** opcje są wyświetlane na **opcji** selektor na **edytora obrazów** paska narzędzi (jak pokazano poniżej).

![Opcje w tle &#45; przezroczystości](../windows/media/vcimageeditoropaqtranspback.gif "vcImageEditorOpaqTranspBack")<br/>
**Opcje przezroczystości i nieprzezroczyste** na **paska narzędzi edytora obrazów**

### <a name="to-switch-between-a-transparent-and-opaque-background"></a>Aby przełączać się między tło przezroczyste i nieprzezroczyste

1. W **edytora obrazów** narzędzi, kliknij przycisk **opcji** selektor, a następnie kliknij odpowiednią tła:

   - `Opaque Background (O)`: Istniejącego obrazu jest zasłonięte przez wszystkie części zaznaczenia.

   - `Transparent Background (T)`: Istniejący obraz pokazuje fragmenty zaznaczenia, które odpowiadają bieżącym kolorem tła.

\- lub —

- Na **obraz** menu, zaznacz lub wyczyść **Rysowanie nieprzezroczystych**.

Możesz zmienić kolor tła zaznaczenia już w trakcie efekt zmiany, które części obrazu są niewidoczne.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Praca z kolorem](../windows/working-with-color-image-editor-for-icons.md)