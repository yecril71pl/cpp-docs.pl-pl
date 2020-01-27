---
title: Aktualizowanie symboli WINVER i _WIN32_WINNT
description: Kiedy i jak aktualizować makra WINVER i _WIN32_WINNT w uaktualnionych projektach programu C++ Visual Studio.
ms.date: 01/22/2020
helpviewer_keywords:
- WINVER in an upgraded Visual Studio C++ project
- _WIN32_WINNT in an upgraded Visual Studio C++ project
ms.assetid: 6a1f1d66-ae0e-48a7-81c3-524d8e8f3447
ms.openlocfilehash: b81c7967732c7b0c23ff0eb73d2a866a9b33713b
ms.sourcegitcommit: b67b08472b6f1ee8f1c5684bba7056d3e0fc745f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76725699"
---
# <a name="update-winver-and-_win32_winnt"></a>Aktualizowanie symboli WINVER i _WIN32_WINNT

Korzystając z Windows SDK można określić wersje systemu Windows, na których można uruchomić kod. Preprocesor makra **winver** i **_WIN32_WINNT** określają minimalną wersję systemu operacyjnego obsługiwaną przez kod. Program Visual Studio i pomoc C++ techniczna kompilatora firmy Microsoft ukierunkowana na system Windows 7 z dodatkiem SP1 lub nowszym. Starsze zestawy narzędzi obejmują obsługę systemu Windows XP z dodatkiem SP4, Windows Server 2003 z dodatkiem SP4, Vista i Windows Server 2008. Systemy Windows 95, Windows 98, Windows ME, Windows NT i Windows 2000 nie są obsługiwane.

W przypadku uaktualniania starszego projektu może być konieczne zaktualizowanie makr w programie **winver** lub **_WIN32_WINNT** . Jeśli są przypisane wartości dla nieobsługiwanej wersji systemu Windows, mogą pojawić się błędy kompilacji dotyczące tych makr.

## <a name="remarks"></a>Uwagi

Aby zmodyfikować makra, w pliku nagłówkowym (na przykład w *targetver. h*, który jest dołączony do niektórych szablonów projektu przeznaczonych dla systemu Windows), Dodaj następujące wiersze.

```C
#define WINVER 0x0A00
#define _WIN32_WINNT 0x0A00
```

Makra w tym przykładzie są ustawiane jako docelowe dla każdej wersji systemu operacyjnego Windows 10. Możliwe wartości są wymienione w pliku nagłówkowym systemu Windows *dołączenie SDKDDKVer. h*, który definiuje makra dla każdej wersji głównej systemu Windows. Aby skompilować aplikację do obsługi poprzedniej platformy systemu Windows, Dołącz *nagłówek WinSDKVer. h*. Następnie należy ustawić makra **winver** i **_WIN32_WINNT** na najstarszej obsługiwanej platformie przed włączeniem *dołączenie SDKDDKVer. h*. Oto wiersze z wersji zestawu SDK systemu Windows 10 *dołączenie SDKDDKVer. h* , które kodują wartości dla każdej wersji głównej systemu Windows:

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

Aby uzyskać bardziej szczegółowe podejście do przechowywania wersji, można użyć stałych wersji NTDDI w *dołączenie SDKDDKVer. h*. Poniżej przedstawiono niektóre makra zdefiniowane przez *dołączenie SDKDDKVer. h* w zestawie SDK systemu Windows 10 w wersji 10.0.18362.0:

```C
//
// NTDDI version constants
//
#define NTDDI_WIN7                          0x06010000
#define NTDDI_WIN8                          0x06020000
#define NTDDI_WINBLUE                       0x06030000
#define NTDDI_WINTHRESHOLD                  0x0A000000  /* ABRACADABRA_THRESHOLD */
#define NTDDI_WIN10                         0x0A000000  /* ABRACADABRA_THRESHOLD */
#define NTDDI_WIN10_TH2                     0x0A000001  /* ABRACADABRA_WIN10_TH2 */
#define NTDDI_WIN10_RS1                     0x0A000002  /* ABRACADABRA_WIN10_RS1 */
#define NTDDI_WIN10_RS2                     0x0A000003  /* ABRACADABRA_WIN10_RS2 */
#define NTDDI_WIN10_RS3                     0x0A000004  /* ABRACADABRA_WIN10_RS3 */
#define NTDDI_WIN10_RS4                     0x0A000005  /* ABRACADABRA_WIN10_RS4 */
#define NTDDI_WIN10_RS5                     0x0A000006  /* ABRACADABRA_WIN10_RS5 */
#define NTDDI_WIN10_19H1                    0x0A000007  /* ABRACADABRA_WIN10_19H1*/

#define WDK_NTDDI_VERSION                   NTDDI_WIN10_19H1 /* ABRACADABRA_WIN10_19H1 */

//
// masks for version macros
//
#define OSVERSION_MASK      0xFFFF0000
#define SPVERSION_MASK      0x0000FF00
#define SUBVERSION_MASK     0x000000FF

//
// macros to extract various version fields from the NTDDI version
//
#define OSVER(Version)  ((Version) & OSVERSION_MASK)
#define SPVER(Version)  (((Version) & SPVERSION_MASK) >> 8)
#define SUBVER(Version) (((Version) & SUBVERSION_MASK) )
```

Makra **OSVER**, **SPVER**i **SUBVER** mogą być używane w kodzie do sterowania kompilacją warunkową dla różnych poziomów obsługi interfejsu API.

Niektóre z tych wersji systemu Windows mogą nie być widoczne na liście w *dołączenie SDKDDKVer. h* . Oznacza to, że prawdopodobnie używasz starszej wersji Windows SDK. Domyślnie nowe projekty systemu Windows w programie Visual Studio używają zestawu SDK systemu Windows 10.

> [!NOTE]
> Wartości nie są gwarantowane, jeśli dołączysz wewnętrzne nagłówki MFC w aplikacji.

Możesz również zdefiniować to makro przy użyciu opcji kompilatora `/D`. Aby uzyskać więcej informacji, zobacz [/d (Definicje preprocesora)](../build/reference/d-preprocessor-definitions.md).

Aby uzyskać więcej informacji na temat znaczenia tych makr, zobacz [Korzystanie z nagłówków systemu Windows](/windows/win32/WinProg/using-the-windows-headers).

## <a name="see-also"></a>Zobacz także

[Historia C++ zmian wizualnych](../porting/visual-cpp-change-history-2003-2015.md)
