# Hacer commits en la rama de la funcionalidad

Los commits deben ser pequeños, descriptivos y referenciar el issue cuando sea posible.

## Pasos
 
1. Realiza cambios en los archivos de tu proyecto (por ejemplo, agrega `lerp` en un archivo de utilidades o ejemplo).
2. Añade los cambios al staging:

```powershell
git add .
```

1. Crea un commit con mensaje significativo y referencia al issue (ejemplo issue #12):

```powershell
git commit -m "feat: implementar lerp(a, b, t); casos base y tests (refs #12)"
```

1. Repite para más cambios. Sube tu rama al remoto:

```powershell
git push -u origin feature/interpolador-lineal
```

---

> Consejo: Prefiere mensajes de commit con prefijos convencionales (feat, fix, docs, refactor).
