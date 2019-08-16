---
title: Funkcje globalne zabezpieczeń
ms.date: 11/04/2016
f1_keywords:
- atlsecurity/ATL::AtlGetDacl
- atlsecurity/ATL::AtlSetDacl
- atlsecurity/ATL::AtlGetGroupSid
- atlsecurity/ATL::AtlSetGroupSid
- atlsecurity/ATL::AtlGetOwnerSid
- atlsecurity/ATL::AtlSetOwnerSid
- atlsecurity/ATL::AtlGetSacl
- atlsecurity/ATL::AtlSetSacl
- atlsecurity/ATL::AtlGetSecurityDescriptor
helpviewer_keywords:
- SIDs [C++], modifying SID objects
- ACL object global functions
- security IDs [C++]
ms.assetid: 6a584bfe-16b7-47f4-8439-9c789c41567a
ms.openlocfilehash: 5f3c0464b239f4500d416b80ae4fdf06c2dc386f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495175"
---
# <a name="security-global-functions"></a>Funkcje globalne zabezpieczeń

Te funkcje zapewniają obsługę modyfikacji identyfikatorów SID i obiektów listy ACL.

> [!IMPORTANT]
>  Funkcje wymienione w poniższej tabeli nie mogą być używane w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

|||
|-|-|
|[AtlGetDacl](#atlgetdacl)|Wywołaj tę funkcję, aby pobrać informacje o poufnej liście kontroli dostępu (DACL) określonego obiektu.|
|[AtlSetDacl](#atlsetdacl)|Wywołaj tę funkcję, aby ustawić informacje o poufnej liście kontroli dostępu (DACL) określonego obiektu.|
|[AtlGetGroupSid](#atlgetgroupsid)|Wywołaj tę funkcję, aby pobrać identyfikator zabezpieczeń grupy (SID) obiektu.|
|[AtlSetGroupSid](#atlsetgroupsid)|Wywołaj tę funkcję, aby ustawić identyfikator zabezpieczeń grupy (SID) obiektu.|
|[AtlGetOwnerSid](#atlgetownersid)|Wywołaj tę funkcję, aby pobrać identyfikator zabezpieczeń właściciela (SID) obiektu.|
|[AtlSetOwnerSid](#atlsetownersid)|Wywołaj tę funkcję, aby ustawić identyfikator zabezpieczeń właściciela (SID) obiektu.|
|[AtlGetSacl](#atlgetsacl)|Wywołaj tę funkcję, aby pobrać informacje o systemowej liście kontroli dostępu (SACL) określonego obiektu.|
|[AtlSetSacl](#atlsetsacl)|Wywołaj tę funkcję, aby ustawić informacje o systemowej liście kontroli dostępu (SACL) określonego obiektu.|
|[AtlGetSecurityDescriptor](#atlgetsecuritydescriptor)|Wywołaj tę funkcję, aby pobrać deskryptor zabezpieczeń danego obiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity. h

##  <a name="atlgetdacl"></a>AtlGetDacl

Wywołaj tę funkcję, aby pobrać informacje o poufnej liście kontroli dostępu (DACL) określonego obiektu.

> [!IMPORTANT]
>  Tej funkcji nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

```
inline bool AtlGetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CDacl* pDacl) throw();
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Dojście do obiektu, dla którego mają zostać pobrane informacje o zabezpieczeniach.

*ObjectType*<br/>
Określa wartość z wyliczenia [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) , która wskazuje typ obiektu identyfikowanego przez parametr *hObject* .

*pDacl*<br/>
Wskaźnik do obiektu DACL, który będzie zawierać pobrane informacje o zabezpieczeniach.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli *hObject* lub *pDacl* jest nieprawidłowy.

##  <a name="atlsetdacl"></a>AtlSetDacl

Wywołaj tę funkcję, aby ustawić informacje o poufnej liście kontroli dostępu (DACL) określonego obiektu.

> [!IMPORTANT]
>  Tej funkcji nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

```
inline bool AtlSetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CDacl& rDacl,
    DWORD dwInheritanceFlowControl = 0) throw(...);
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Dojście do obiektu, dla którego chcesz ustawić informacje o zabezpieczeniach.

*ObjectType*<br/>
Określa wartość z wyliczenia [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) , która wskazuje typ obiektu identyfikowanego przez parametr *hObject* .

*rDacl*<br/>
Lista DACL zawierająca nowe informacje o zabezpieczeniach.

*dwInheritanceFlowControl*<br/>
Sterowanie przepływem dziedziczenia. Ta wartość może być równa 0 (domyślna), PROTECTED_DACL_SECURITY_INFORMATION lub UNPROTECTED_DACL_SECURITY_INFORMATION.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli *hObject* jest nieprawidłowy, lub jeśli *dwInheritanceFlowControl* nie jest jedną z trzech dozwolonych wartości.
### <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity. h

##  <a name="atlgetgroupsid"></a>AtlGetGroupSid

Wywołaj tę funkcję, aby pobrać identyfikator zabezpieczeń grupy (SID) obiektu.

> [!IMPORTANT]
>  Tej funkcji nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

```
inline bool AtlGetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Dojście do obiektu, z którego mają zostać pobrane informacje o zabezpieczeniach.

*ObjectType*<br/>
Określa wartość z wyliczenia [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) , która wskazuje typ obiektu identyfikowanego przez parametr *hObject* .

*Pusty PSID*<br/>
Wskaźnik do `CSid` obiektu, który będzie zawierać nowe informacje o zabezpieczeniach.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity. h

##  <a name="atlsetgroupsid"></a>AtlSetGroupSid

Wywołaj tę funkcję, aby ustawić identyfikator zabezpieczeń grupy (SID) obiektu.

> [!IMPORTANT]
>  Tej funkcji nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

```
inline bool AtlSetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Dojście do obiektu, dla którego chcesz ustawić informacje o zabezpieczeniach.

*ObjectType*<br/>
Określa wartość z wyliczenia [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) , która wskazuje typ obiektu identyfikowanego przez parametr *hObject* .

*rSid*<br/>
`CSid` Obiekt zawierający nowe informacje o zabezpieczeniach.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity. h

##  <a name="atlgetownersid"></a>AtlGetOwnerSid

Wywołaj tę funkcję, aby pobrać identyfikator zabezpieczeń właściciela (SID) obiektu.

> [!IMPORTANT]
>  Tej funkcji nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

```
inline bool AtlGetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Dojście do obiektu, z którego mają zostać pobrane informacje o zabezpieczeniach.

*ObjectType*<br/>
Określa wartość z wyliczenia [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) , która wskazuje typ obiektu identyfikowanego przez parametr *hObject* .

*Pusty PSID*<br/>
Wskaźnik do `CSid` obiektu, który będzie zawierać nowe informacje o zabezpieczeniach.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity. h

##  <a name="atlsetownersid"></a>AtlSetOwnerSid

Wywołaj tę funkcję, aby ustawić identyfikator zabezpieczeń właściciela (SID) obiektu.

> [!IMPORTANT]
>  Tej funkcji nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

```
inline bool AtlSetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Dojście do obiektu, dla którego chcesz ustawić informacje o zabezpieczeniach.

*ObjectType*<br/>
Określa wartość z wyliczenia [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) , która wskazuje typ obiektu identyfikowanego przez parametr *hObject* .

*rSid*<br/>
`CSid` Obiekt zawierający nowe informacje o zabezpieczeniach.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity. h

##  <a name="atlgetsacl"></a>AtlGetSacl

Wywołaj tę funkcję, aby pobrać informacje o systemowej liście kontroli dostępu (SACL) określonego obiektu.

> [!IMPORTANT]
>  Tej funkcji nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

```
inline bool AtlGetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSacl* pSacl,
    bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Dojście do obiektu, z którego mają zostać pobrane informacje o zabezpieczeniach.

*ObjectType*<br/>
Określa wartość z wyliczenia [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) , która wskazuje typ obiektu identyfikowanego przez parametr *hObject* .

*pSacl*<br/>
Wskaźnik do obiektu SACL, który będzie zawierać pobrane informacje o zabezpieczeniach.

*bRequestNeededPrivileges*<br/>
W przypadku wartości true funkcja podejmie próbę włączenia uprawnienia SE_SECURITY_NAME i przywrócenia jej po zakończeniu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

Jeśli `AtlGetSacl` ma być wywoływana wiele razy w wielu różnych obiektach, będzie bardziej wydajna, aby włączyć uprawnienie SE_SECURITY_NAME raz przed wywołaniem funkcji, z *bRequestNeededPrivilegesem* ustawionym na wartość false.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity. h

##  <a name="atlsetsacl"></a>AtlSetSacl

Wywołaj tę funkcję, aby ustawić informacje o systemowej liście kontroli dostępu (SACL) określonego obiektu.

> [!IMPORTANT]
>  Tej funkcji nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

```
inline bool AtlSetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSacl& rSacl,
    DWORD dwInheritanceFlowControl = 0,
    bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Dojście do obiektu, dla którego chcesz ustawić informacje o zabezpieczeniach.

*ObjectType*<br/>
Określa wartość z wyliczenia [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) , która wskazuje typ obiektu identyfikowanego przez parametr *hObject* .

*rSacl*<br/>
Lista SACL zawierająca nowe informacje o zabezpieczeniach.

*dwInheritanceFlowControl*<br/>
Sterowanie przepływem dziedziczenia. Ta wartość może być równa 0 (domyślna), PROTECTED_SACL_SECURITY_INFORMATION lub UNPROTECTED_SACL_SECURITY_INFORMATION.

*bRequestNeededPrivileges*<br/>
W przypadku wartości true funkcja podejmie próbę włączenia uprawnienia SE_SECURITY_NAME i przywrócenia jej po zakończeniu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli *hObject* jest nieprawidłowy, lub jeśli *dwInheritanceFlowControl* nie jest jedną z trzech dozwolonych wartości.

Jeśli `AtlSetSacl` ma być wywoływana wiele razy w wielu różnych obiektach, będzie bardziej wydajna, aby włączyć uprawnienie SE_SECURITY_NAME raz przed wywołaniem funkcji, z *bRequestNeededPrivilegesem* ustawionym na wartość false.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity. h

##  <a name="atlgetsecuritydescriptor"></a>AtlGetSecurityDescriptor

Wywołaj tę funkcję, aby pobrać deskryptor zabezpieczeń danego obiektu.

> [!IMPORTANT]
>  Tej funkcji nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

```
inline bool AtlGetSecurityDescriptor(
    LPCTSTR pszObjectName,
    SE_OBJECT_TYPE ObjectType,
    CSecurityDesc* pSecurityDescriptor,
    SECURITY_INFORMATION requestedInfo = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION,
bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>Parametry

*pszObjectName*<br/>
Wskaźnik na ciąg zakończony znakiem null, który określa nazwę obiektu, z którego mają zostać pobrane informacje o zabezpieczeniach.

*ObjectType*<br/>
Określa wartość z wyliczenia [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) , która wskazuje typ obiektu identyfikowanego przez parametr *pszObjectName* .

*pSecurityDescriptor*<br/>
Obiekt, który odbiera żądany deskryptor zabezpieczeń.

*requestedInfo*<br/>
Zestaw flag [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) bit, które wskazują typ informacji o zabezpieczeniach do pobrania. Ten parametr może być kombinacją następujących wartości.

*bRequestNeededPrivileges*<br/>
W przypadku wartości true funkcja podejmie próbę włączenia uprawnienia SE_SECURITY_NAME i przywrócenia jej po zakończeniu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

Jeśli `AtlGetSecurityDescriptor` ma być wywoływana wiele razy w wielu różnych obiektach, będzie bardziej wydajna, aby włączyć uprawnienie SE_SECURITY_NAME raz przed wywołaniem funkcji, z *bRequestNeededPrivilegesem* ustawionym na wartość false.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity. h

## <a name="see-also"></a>Zobacz także

[Funkcje](../../atl/reference/atl-functions.md)
