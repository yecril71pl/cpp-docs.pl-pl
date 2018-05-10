---
title: Modyfikowanie symboli WINVER i _WIN32_WINNT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/04/2017
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- WINVER in an upgraded Visual C++ project
- _WIN32_WINNT in an upgraded Visual C++ project
ms.assetid: 6a1f1d66-ae0e-48a7-81c3-524d8e8f3447
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4007f8b07b78618f4fdd8031d0f6dab5f1c12916
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="modifying-winver-and-win32winnt"></a>Modyfikowanie symboli WINVER i _WIN32_WINNT

Visual C++ nie obsługuje już docelowy system operacyjny Windows 95, Windows 98, Windows ME, Windows NT lub Windows 2000. Jeśli Twoje **WINVER** lub **_WIN32_WINNT** makra są przypisane do jednej z tych wersji systemu Windows, należy zmodyfikować makra. Podczas uaktualniania projektu, który został utworzony przy użyciu starszej wersji programu Visual C++, mogą zostać wyświetlone błędy kompilacji powiązane z **WINVER** lub **_WIN32_WINNT** makra, jeśli są przypisane do wersji W przypadku systemu Windows, który nie jest już obsługiwana.  
  
## <a name="remarks"></a>Uwagi  

Aby zmodyfikować makra, w pliku nagłówka (na przykład targetver.h znajdującą się podczas tworzenia projektu, którego celem jest system Windows), Dodaj następujące wiersze.  
  
```C  
#define WINVER 0x0A00  
#define _WIN32_WINNT 0x0A00  
```  
  
To jest przeznaczony dla systemu operacyjnego Windows 10. Te wartości są wymienione w pliku nagłówka Windows nagłówka SDKDDKVer.h, definiującą makra dla każdej wersji systemu Windows. Należy dodać #define przed dołączeniem nagłówka SDKDDKVer.h. Poniżej przedstawiono wiersze z wersji Windows 10 nagłówka SDKDDKVer.h kodowania wartości dla każdej wersji systemu Windows:  
  
```C  
//  
// _WIN32_WINNT version constants  
//  
#define _WIN32_WINNT_NT4                    0x0400 // Windows NT 4.0  
#define _WIN32_WINNT_WIN2K                  0x0500 // Windows 2000  
#define _WIN32_WINNT_WINXP                  0x0501 // Windows XP  
#define _WIN32_WINNT_WS03                   0x0502 // Windows Server 2003  
#define _WIN32_WINNT_WIN6                   0x0600 // Windows Vista  
#define _WIN32_WINNT_VISTA                  0x0600 // Windows Vista  
#define _WIN32_WINNT_WS08                   0x0600 // Windows Server 2008  
#define _WIN32_WINNT_LONGHORN               0x0600 // Windows Vista  
#define _WIN32_WINNT_WIN7                   0x0601 // Windows 7  
#define _WIN32_WINNT_WIN8                   0x0602 // Windows 8  
#define _WIN32_WINNT_WINBLUE                0x0603 // Windows 8.1  
#define _WIN32_WINNT_WINTHRESHOLD           0x0A00 // Windows 10  
#define _WIN32_WINNT_WIN10                  0x0A00 // Windows 10  
```  
  
Jeśli nie widzisz wszystkich wersji systemu Windows wymienionych w kopię nagłówka SDKDDKVer.h, które są prawdopodobnie używasz starszej wersji zestawu Windows SDK. Domyślnie Win32 projekty w programie Visual Studio 2017 używają zestawu Windows 10 SDK.   
  
> [!NOTE]
>  Wartości nie ma gwarancji działać, jeśli zawiera wewnętrzny nagłówków MFC w aplikacji.  
  
Można również definiować to makro za pomocą **/D** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [/D (definicje preprocesora)](../build/reference/d-preprocessor-definitions.md).  
  
Aby uzyskać więcej informacji na temat znaczenia tych makr, zobacz [korzystanie z nagłówków systemu Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).  
  
## <a name="see-also"></a>Zobacz też  

[Historia zmian w usłudze Visual C++](..\porting\visual-cpp-change-history-2003-2015.md)
