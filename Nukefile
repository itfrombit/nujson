;;
;; Nukefile for NuJSON
;;
;; Commands:
;;	nuke 		- builds NuJSON as a framework
;;	nuke test	- runs the unit tests in the NuTests directory
;;	nuke install	- installs NuJSON in /Library/Frameworks
;;	nuke clean	- removes build artifacts
;;	nuke clobber	- removes build artifacts and NuJSON.framework
;;
;; The "nuke" build tool is installed with Nu (http://programming.nu)
;;

;; the @variables below are instance variables of a NukeProject.
;; for details, see tools/nuke in the Nu source distribution.

;; source files
(set @m_files     (filelist "^objc/.*.m$"))

;; framework description
(set @framework "NuJSON")
(set @framework_identifier   "nu.programming.json")
(set @framework_creator_code "????")

(set @cflags "-g -fobjc-gc -std=gnu99 -I Source")
(set @ldflags "-framework Foundation")

(compilation-tasks)
(framework-tasks)

(task "clobber" => "clean" is
      (SH "rm -rf #{@framework_dir}")) ;; @framework_dir is defined by the nuke framework-tasks macro

(task "default" => "framework")

(task "install" => "framework" is
      (SH "sudo rm -rf /Library/Frameworks/#{@framework}.framework")
      (SH "ditto #{@framework}.framework /Library/Frameworks/#{@framework}.framework"))

(task "test" => "framework" is
      (SH "nutest test/test_*.nu"))
