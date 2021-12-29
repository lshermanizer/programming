
```
##### Emacs setting
;;save all back-up files into one directory
(setq backup-directory-alist `(("." . "~/.saves")))
;;set font size
(set-face-attribute 'default nil :height 85)
;;select and backspace to delete
(delete-selection-mode t)
;;add line number
(add-hook 'prog-mode-hook 'linum-mode)
(custom-set-variables
  ;; custom-set-variables was added by Custom.
  ;; If you edit it by hand, you could mess it up, so be careful.
  ;; Your init file should contain only one such instance.
  ;; If there is more than one, they won't work right.
 '(inhibit-startup-screen t))
(custom-set-faces
  ;; custom-set-faces was added by Custom.
  ;; If you edit it by hand, you could mess it up, so be careful.
  ;; Your init file should contain only one such instance.
  ;; If there is more than one, they won't work right.
 )
 ```
