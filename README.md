<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">

</head>
<body>
  <h1>Industrial_Robotics_Gym - Proyecto PyBullet</h1>

  <p><strong>Descripción:</strong><br>
  Este proyecto tiene como objetivo utilizar <code>Industrial_Robotics_Gym</code> junto con PyBullet para la simulación de robots industriales. Se trabajó dentro de un contenedor Docker para mantener un entorno limpio y controlado.</p>

  <h2>Pasos realizados</h2>
  <ul>
    <li>Se eliminaron instalaciones previas y carpetas corruptas de <code>/app/src/Industrial_Robotics_Gym</code> y <code>/app/RoLE</code>.</li>
    <li>Se clonó correctamente el repositorio <code>Industrial_Robotics_Gym</code> dentro de <code>/app/src</code>.</li>
    <li>Se configuró la variable de entorno <code>PYTHONPATH</code>:
      <pre>export PYTHONPATH="/app:$PYTHONPATH"</pre>
    </li>
    <li>Se identificó que <code>Industrial_Robotics_Gym</code> depende del módulo <code>RoLE</code> para los parámetros de los robots.</li>
    <li>Se intentó descargar <code>RoLE</code> mediante <code>git clone</code> y <code>curl + unzip</code>, pero las descargas fallaron debido a errores 404 o archivos corruptos.</li>
    <li>Como solución temporal:
      <ul>
        <li>Se comentó la línea <code>import RoLE.Parameters.Robot as Parameters</code> en <code>__init__.py</code>.</li>
        <li>Se reemplazó <code>CONST_ROBOT_TYPE</code> por una lista vacía <code>[]</code> para evitar errores de sintaxis.</li>
      </ul>
    </li>
    <li>Se probó la carga del entorno con:
      <pre>
from src.Industrial_Robotics_Gym.Environment.Core import Industrial_Robotics_Gym_Env_Cls
env = Industrial_Robotics_Gym_Env_Cls(mode="Default")
      </pre>
      El entorno se inicia, pero <strong>no se pueden definir ni simular robots</strong> debido a la falta de <code>RoLE</code>.
    </li>
  </ul>

  <h2>Estado actual</h2>
  <ul>
    <li>El proyecto puede crear un entorno básico en PyBullet.</li>
    <li>No es posible ejecutar simulaciones completas porque la dependencia <code>RoLE</code> no se puede instalar actualmente.</li>
  </ul>

  <h2>Próximos pasos para la ejecución completa</h2>
  <ol>
    <li>Obtener acceso al repositorio <code>RoLE</code> válido.</li>
    <li>Instalar <code>RoLE</code> dentro del contenedor Docker.</li>
    <li>Restaurar la importación de <code>Parameters</code> y la lista de robots en <code>__init__.py</code>.</li>
    <li>Ejecutar de nuevo el entorno y verificar la simulación de robots.</li>
  </ol>

  <h2>Conclusión</h2>
  <p>
  El proyecto está parcialmente funcional y documenta todos los pasos realizados, así como los bloqueos encontrados debido a la dependencia <code>RoLE</code>.
  </p>
</body>
</html>
