---
title: Modyfikowanie symboli WINVER i _WIN32_WINNT
ms.date: 09/04/2017
helpviewer_keywords:
- WINVER in an upgraded Visual Studio C++ project
- _WIN32_WINNT in an upgraded Visual Studio C++ project
ms.assetid: 6a1f1d66-ae0e-48a7-81c3-524d8e8f3447
ms.openlocfilehash: a83e92444e7010e4d3b65153b2e60e1c5d952cef
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511606"
---
# <a name="modifying-winver-and-_win32_winnt"></a>Modyfikowanie symboli WINVER i _WIN32_WINNT

Wizualizacja C++ nie obsługuje już systemu Windows 95, Windows 98, Windows Me, Windows NT ani Windows 2000. Jeśli makra **winver** lub **_WIN32_WINNT** są przypisane do jednej z tych wersji systemu Windows, należy zmodyfikować makra. W przypadku uaktualniania projektu, który został utworzony przy użyciu wcześniejszej wersji wizualizacji C++, można zobaczyć błędy kompilacji związane z makrami **winver** lub **_WIN32_WINNT** , jeśli są przypisane do wersji systemu Windows, która nie jest już obsługiwana.

## <a name="remarks"></a>Uwagi

Aby zmodyfikować makra, w pliku nagłówkowym (na przykład targetver. h, który jest dołączany podczas tworzenia projektu, który jest przeznaczony dla systemu Windows), Dodaj następujące wiersze.

```C
#define WINVER 0x0A00
#define _WIN32_WINNT 0x0A00
```

Jest to przeznaczony dla systemu operacyjnego Windows 10. Te wartości są wymienione w pliku nagłówkowym systemu Windows dołączenie SDKDDKVer. h, który definiuje także makra dla każdej wersji systemu Windows. Przed dołączeniem dołączenie SDKDDKVer. h należy dodać instrukcję #define. Oto wiersze z wersji systemu Windows 10 dołączenie SDKDDKVer. h, które kodują wartości dla każdej wersji systemu Windows:

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

Jeśli wszystkie te wersje systemu Windows nie są widoczne na liście w kopii dołączenie SDKDDKVer. h, prawdopodobnie używasz starszej wersji Windows SDK. Domyślnie projekty Win32 w programie Visual Studio 2017 używają zestawu SDK systemu Windows 10.

> [!NOTE]
> Wartości nie są gwarantowane, jeśli dołączysz wewnętrzne nagłówki MFC w aplikacji.

Możesz również zdefiniować to makro przy użyciu `/D` opcji kompilatora. Aby uzyskać więcej informacji, zobacz [/d (Definicje preprocesora)](../build/reference/d-preprocessor-definitions.md).

Aby uzyskać więcej informacji na temat znaczenia tych makr, zobacz [Korzystanie z nagłówków systemu Windows](/windows/win32/WinProg/using-the-windows-headers).

## <a name="see-also"></a>Zobacz także

[Historia C++ zmian wizualnych](../porting/visual-cpp-change-history-2003-2015.md)
