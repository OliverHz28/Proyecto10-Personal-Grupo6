
## **Descripcion:**
Repositorio donde documento mis contribuciones al `Proyecto 10: Pull requests y revisión de código Automatizada con Hooks y Linters` en sus respectivas ramas.

### **Sprint 1**
#### Demostracion en video
[Sprint 1 (Dia 3: 9/06/2025) Grupo 6 Proyecto 10 ](https://www.youtube.com/watch?v=ZwcuikAZ56w)
#### **Mi Rol**
* Responsable de iniciar el repositorio de Git y establecer la estructura de carpetas que necesitaremos para el proyecto. Esto incluye `src/` para el codigo en Python, `scripts/` para los scripts de automatización, `tests`/ para nuestras pruebas, `.github/workflows/` para las GitHub Actions, y `pr_simulation/` para simular los Pull Requests."

    ```
        .
        ├───.github/
                └── workflows/
                    └── pr_validation
        ├─── scripts/
                └── lint_all.sh
        ├─── src/
                └── config_modifier.py
        ├─── tests/
                └── test_config_modifier.py
        ├─── pr_simulation/
                └── .gitkeep
        └── README.md
    ```

* Desarrollar `config_modifier.py` `en src/` para el [Issue #4](https://github.com/OliverHz28/PC3Proyecto10/issues/4)

    ```python
    import json
    import os


    def leer_json(file_path):
        """
        Lee el archivo JSON desde el sistema de archivos y
        devuelve su contenido como un diccionario
        """

        if not os.path.exists(file_path):
            raise FileNotFoundError(f"No existe el archivo '{file_path}'")

        with open(file_path, 'r', encoding='utf-8') as f:
            try:
                return json.load(f)
            except json.JSONDecodeError:
                raise ValueError(f"El archivo '{file_path}' no contiene un JSON válido")


    def incrementar_version(file_path):
        """
        Incrementa el campo "version" del archivo JSON
        """

        config = leer_json(file_path)

        if "version" not in config:
            raise KeyError("No existe el campo 'version' en el archivo JSON")

        if not isinstance(config['version'], (int, float)):
            raise TypeError("El campo 'version' no es un número")

        config["version"] += 1
        with open(file_path, 'w', encoding='utf-8') as f:
            json.dump(config, f, indent=4)
        return config["version"]

    ```

#### [**Contribucciones**](CONTRIBUTIONS.md)

