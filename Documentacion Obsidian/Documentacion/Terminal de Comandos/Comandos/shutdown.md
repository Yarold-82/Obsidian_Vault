Para forzar el cierre de las aplicaciones y reiniciar la computadora local después de un retraso de un minuto, con el motivo Aplicación: Mantenimiento (planificado) y el comentario “Reconfiguración de miapp.exe”.

shutdown /r /t 60 /c "Reconfiguración miapp.exe" /f /d p:4:1

Para reiniciar la computadora remota mi_servidor_remoto con los mismos parámetros que en el ejemplo anterior:

shutdown /r /m \mi_servidor_remoto /t 60 /c "Reconfiguración miapp.exe" /f /d p:4:1