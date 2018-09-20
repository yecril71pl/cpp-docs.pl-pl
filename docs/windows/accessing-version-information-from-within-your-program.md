---
title: Uzyskiwanie dostępu do informacji o wersji z Twojego programu (C++) | Dokumentacja firmy Microsoft
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
- VerQueryValue
- version information, accessing from within programs
- GetFileVersionInfo
- version information
ms.assetid: 18622333-d9e8-4309-9465-677cd10c79b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ac344242a55ba9d2f3c6ec2846feb18f70bf6483
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421521"
---
# <a name="accessing-version-information-from-within-your-program-c"></a>Uzyskiwanie dostępu do informacji o wersji z Twojego programu (C++)

### <a name="to-access-version-information-from-within-your-program"></a>Aby uzyskać dostęp do informacji o wersji z Twojego programu

1. Aby uzyskać dostęp do informacji o wersji z Twojego programu, należy użyć [GetFileVersionInfo](/windows/desktop/api/winver/nf-winver-getfileversioninfoa) funkcji i [VerQueryValue](/windows/desktop/api/winver/nf-winver-verqueryvaluea) funkcji.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytor informacji o wersji](../windows/version-information-editor.md)<br/>
[Informacje o wersji (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)