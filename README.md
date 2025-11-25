# moodle501-plugins
Plugins for Moodle 5.1

[![Update Submodules](https://github.com/AdrianoRuseler/moodle501-plugins/actions/workflows/update-submodules.yml/badge.svg)](https://github.com/AdrianoRuseler/moodle501-plugins/actions/workflows/update-submodules.yml)

## Moodle Update (TODO: public folder)
```bash
export MDLREPO="https://github.com/moodle/moodle.git"
export MDLBRANCH="MOODLE_501_STABLE"  # GIT Branch for moodle core
export MDLCORE="mdlcore" # Temp folder for moodle core
export PLGREPO="https://github.com/AdrianoRuseler/moodle501-plugins.git"
export PLGBRANCH="main" # GIT Branch for moodle plugins
export MDLPLGS="mdlplugins" # Temp folder for moodle plugins
# Moodle software (For example, everything in server/htdocs/moodle)
export MDLHOME="path/to/moodle" # TODO!

cd /tmp
git clone --depth=1 --branch=$MDLBRANCH $MDLREPO $MDLCORE
git clone --depth=1 --recursive --branch=$PLGBRANCH $PLGREPO $MDLPLGS
sudo rsync -a /tmp/$MDLPLGS/moodle/* /tmp/$MDLCORE/
	
echo "Moving old files ..."
sudo mv $MDLHOME $MDLHOME.tmpbkp
mkdir $MDLHOME

echo "moving new files..."
sudo mv /tmp/$MDLCORE/* $MDLHOME

echo "Copying config file ..."
sudo cp $MDLHOME.tmpbkp/config.php $MDLHOME

echo "Remove tmp files..."
sudo rm -rf $MDLHOME.tmpbkp
sudo rm -rf /tmp/$MDLPLGS
sudo rm -rf /tmp/$MDLCORE
```
## Moodle config.php
- https://docs.moodle.org/501/en/Configuration_file

``` php
// Use the following flag to completely disable the installation of plugins
// (new plugins, available updates and missing dependencies) and related
// features (such as cancelling the plugin installation or upgrade) via the
// server administration web interface.
$CFG->disableupdateautodeploy = true;
// Disabling update notifications
$CFG->disableupdatenotifications = true;

// Some administration options allow setting the path to executable files. This can
// potentially cause a security risk. Set this option to true to disable editing
// those config settings via the web. They will need to be set explicitly in the
// config.php file
$CFG->preventexecpath = true;

// Configuring Moodle
$CFG->routerconfigured = true;
```

## Plugins List!  Imported from 500 - (TODO: public folder)!

### MOD

- https://github.com/danmarsden/moodle-mod_attendance/
```bash
git submodule add -b MOODLE_500_STABLE https://github.com/danmarsden/moodle-mod_attendance.git mod/attendance
```
- https://github.com/ndunand/moodle-mod_choicegroup
```bash
git submodule add -b master https://github.com/ndunand/moodle-mod_choicegroup.git mod/choicegroup
```
- https://github.com/frankkoch/moodle-mod_studentquiz
```bash
git submodule add -b main https://github.com/frankkoch/moodle-mod_studentquiz.git mod/studentquiz
```
- https://github.com/xow/moodle-mod_quizgame
```bash
git submodule add -b master https://github.com/xow/moodle-mod_quizgame.git mod/quizgame
```
- https://github.com/jcrodriguez-dis/moodle-mod_vpl
```bash
git submodule add -b master https://github.com/jcrodriguez-dis/moodle-mod_vpl.git mod/vpl
```
- https://github.com/davosmith/moodle-checklist
```bash
git submodule add -b master https://github.com/davosmith/moodle-checklist.git mod/checklist
```
- https://github.com/projectestac/moodle-mod_geogebra
```bash
git submodule add -b master https://github.com/projectestac/moodle-mod_geogebra.git mod/geogebra
```
- https://github.com/academic-moodle-cooperation/moodle-mod_publication
```bash
git submodule add -b MOODLE_405_STABLE https://github.com/academic-moodle-cooperation/moodle-mod_publication.git mod/publication
```
- https://github.com/markn86/moodle-mod_customcert
```bash
git submodule add -b MOODLE_500_STABLE https://github.com/markn86/moodle-mod_customcert.git mod/customcert
```
- https://github.com/bostelm/moodle-mod_scheduler
```bash
git submodule add -b master https://github.com/bostelm/moodle-mod_scheduler.git mod/scheduler
```
- https://github.com/moodleworkplace/moodle-mod_coursecertificate
```bash
git submodule add -b MOODLE_500_STABLE https://github.com/moodleworkplace/moodle-mod_coursecertificate.git mod/coursecertificate
```

- https://github.com/mudrd8mz/moodle-mod_subcourse
```bash
git submodule add -b MOODLE_405_STABLE https://github.com/mudrd8mz/moodle-mod_subcourse.git mod/subcourse
```
- https://github.com/ecampbell/moodle-booktool_wordimport
```bash
git submodule add -b master https://github.com/ecampbell/moodle-booktool_wordimport.git mod/book/tool/wordimport
```
TODO:
- https://github.com/h5p/h5p-moodle-plugin
```bash
git submodule add -b stable https://github.com/h5p/h5p-moodle-plugin.git mod/hvp
cd mod/hvp
git submodule update --init
cd ../..
```
- https://github.com/udima-university/moodle-mod_jitsi
```bash
git submodule add -b master https://github.com/udima-university/moodle-mod_jitsi.git mod/jitsi
```

### TINY
- https://github.com/srobotta/moodle-tiny_cloze
```bash
git submodule add -b main https://github.com/srobotta/moodle-tiny_cloze.git lib/editor/tiny/plugins/cloze
```
- https://github.com/bfh/moodle-tiny_fontcolor
```bash
git submodule add -b main https://github.com/bfh/moodle-tiny_fontcolor.git lib/editor/tiny/plugins/fontcolor
```

- https://github.com/dthies/moodle-tiny_preview
```bash
git submodule add -b main https://github.com/dthies/moodle-tiny_preview.git lib/editor/tiny/plugins/preview
```
- https://codeberg.org/linos/moodle-tiny_wordimport
```bash
git submodule add -b main https://codeberg.org/linos/moodle-tiny_wordimport.git lib/editor/tiny/plugins/wordimport
```

### BLOCK

- https://github.com/FMCorz/moodle-block_xp
```bash
git submodule add -b master https://github.com/FMCorz/moodle-block_xp.git blocks/xp
```

- https://github.com/deraadt/moodle-block_completion_progress
```bash
git submodule add -b master https://github.com/deraadt/moodle-block_completion_progress.git blocks/completion_progress
```

- https://github.com/catalyst/moodle-block_dedication
```bash
git submodule add -b MOODLE_404_STABLE https://github.com/catalyst/moodle-block_dedication.git blocks/dedication
```

- https://github.com/donhinkelman/moodle-block_sharing_cart
```bash
git submodule add -b master https://github.com/donhinkelman/moodle-block_sharing_cart.git blocks/sharing_cart
```

- https://github.com/remotelearner/moodle-block_grade_me
```bash
git submodule add -b MOODLE_405_STABLE https://github.com/remotelearner/moodle-block_grade_me.git blocks/grade_me
```

### REPORT
- https://github.com/catalyst/moodle-report_coursesize
```bash
git submodule add -b MOODLE_401_STABLE https://github.com/catalyst/moodle-report_coursesize.git report/coursesize
```

- https://github.com/mikasmart/moodle-report_benchmark
```bash
git submodule add -b master https://github.com/mikasmart/moodle-report_benchmark.git report/benchmark
```
- https://github.com/catalyst/moodle-report_allbackups

```bash
git submodule add -b MOODLE_404_STABLE https://github.com/catalyst/moodle-report_allbackups.git report/allbackups
```

- https://github.com/moodleou/moodle-report_customsql
```bash
git submodule add -b main https://github.com/moodleou/moodle-report_customsql.git report/customsql
```
### AVAILABILITY
- https://github.com/ewallah/moodle-availability_relativedate
```bash
git submodule add -b MOODLE_500_STABLE https://github.com/ewallah/moodle-availability_relativedate.git availability/condition/relativedate
```

- https://github.com/bdecentgmbh/moodle-availability_sectioncompleted
```bash
git submodule add -b main https://github.com/bdecentgmbh/moodle-availability_sectioncompleted.git availability/condition/sectioncompleted
```

- https://github.com/MFreakNL/moodle-availability_ipaddress
```bash
git submodule add -b main https://github.com/MFreakNL/moodle-availability_ipaddress.git availability/condition/ipaddress
```
### QTYPE
- https://github.com/moodleou/moodle-qtype_oumultiresponse
```bash
git submodule add -b main https://github.com/moodleou/moodle-qtype_oumultiresponse.git question/type/oumultiresponse
```

- https://gricad-gitlab.univ-grenoble-alpes.fr/moodle-plugins/moodle-qtype_vplquestion
```bash
git submodule add -b master https://gricad-gitlab.univ-grenoble-alpes.fr/moodle-plugins/moodle-qtype_vplquestion.git question/type/vplquestion
```
- https://github.com/moodleou/moodle-qtype_combined
```bash
git submodule add -b main https://github.com/moodleou/moodle-qtype_combined.git question/type/combined
```

- https://github.com/gbateson/moodle-qtype_essayautograde
```bash
git submodule add -b master https://github.com/gbateson/moodle-qtype_essayautograde.git question/type/essayautograde
```

- https://github.com/trampgeek/moodle-qtype_coderunner
```bash
git submodule add -b master https://github.com/trampgeek/moodle-qbehaviour_adaptive_adapted_for_coderunner.git question/behaviour/adaptive_adapted_for_coderunner
git submodule add -b master https://github.com/trampgeek/moodle-qtype_coderunner.git question/type/coderunner
```
-->qtype_coderunner
Default exception handler: Erro ao escrever na base de dados Debug: Column 'parent' cannot be null

- https://github.com/moodleou/moodle-qtype_pmatch
- https://github.com/moodleou/moodle-qtype_varnumunit
```bash
git submodule add -b main https://github.com/moodleou/moodle-qtype_pmatch.git question/type/pmatch
git submodule add -b main https://github.com/moodleou/moodle-qtype_varnumericset.git question/type/varnumericset
git submodule add -b main https://github.com/moodleou/moodle-qtype_varnumeric.git question/type/varnumeric
git submodule add -b main https://github.com/moodleou/moodle-qtype_varnumunit.git question/type/varnumunit
git submodule add -b main https://github.com/moodleou/moodle-editor_ousupsub.git lib/editor/ousupsub
```

### ADMIN
- https://github.com/moodleworkplace/moodle-tool_certificate
```bash
git submodule add -b MOODLE_500_STABLE https://github.com/moodleworkplace/moodle-tool_certificate.git admin/tool/certificate
```
- https://github.com/Syxton/moodle-tool_coursearchiver
```bash
git submodule add -b master https://github.com/Syxton/moodle-tool_coursearchiver.git admin/tool/coursearchiver
```
- https://github.com/moodlehq/moodle-tool_migratehvp2h5p
```bash
git submodule add -b main https://github.com/moodlehq/moodle-tool_migratehvp2h5p.git admin/tool/migratehvp2h5p
```
- https://github.com/catalyst/moodle-tool_trigger
```bash
git submodule add -b MOODLE_404_STABLE https://github.com/catalyst/moodle-tool_trigger.git admin/tool/trigger
```
- https://github.com/catalyst/moodle-tool_dynamic_cohorts
```bash
git submodule add -b MOODLE_404_STABLE https://github.com/catalyst/moodle-tool_dynamic_cohorts.git admin/tool/dynamic_cohorts
```
- https://github.com/moodle-an-hochschulen/moodle-tool_redis
```bash
git submodule add -b MOODLE_500_STABLE https://github.com/moodle-an-hochschulen/moodle-tool_redis.git admin/tool/redis
```

### ENROL

### TO REMOVE:

- https://github.com/bobopinna/moodle-enrol_autoenrol
```bash
git submodule add -b master https://github.com/bobopinna/moodle-enrol_autoenrol.git enrol/autoenrol
```

- https://github.com/bynare/moodle-enrol_auto
```bash
git submodule add -b main https://github.com/bynare/moodle-enrol_auto.git enrol/auto
```

### FORMAT

- https://github.com/DigiDago/moodle-format_softcourse
```bash
git submodule add -b MOODLE_501_STABLE https://github.com/DigiDago/moodle-format_softcourse.git course/format/softcourse
```

- https://bitbucket.org/dw8/moodle-format_tiles
```bash
git submodule add -b moodle51 https://bitbucket.org/dw8/moodle-format_tiles.git course/format/tiles
```

- https://gitlab.com/drlikm/format_etask
```bash
git submodule add -b FORMAT_ETASK_24_STABLE https://gitlab.com/drlikm/format_etask.git course/format/etask
```

### THEME

- https://github.com/gjbarnard/moodle-theme_adaptable
```bash
git submodule add -b main https://github.com/gjbarnard/moodle-theme_adaptable.git theme/adaptable
```
- https://github.com/moodle-an-hochschulen/moodle-theme_boost_union
```bash
git submodule add -b MOODLE_500_STABLE https://github.com/moodle-an-hochschulen/moodle-theme_boost_union.git theme/boost_union
```

###   FILTER
- https://github.com/trampgeek/moodle-filter_ace_inline
```bash
git submodule add -b main https://github.com/trampgeek/moodle-filter_ace_inline.git filter/ace_inline
```
### PLAGIARISM

- https://github.com/turnitin/moodle-plagiarism_turnitin
```bash
git submodule add -b develop https://github.com/turnitin/moodle-plagiarism_turnitin.git plagiarism/turnitin
```

- https://github.com/turnitin/moodle-plagiarism_turnitinsim

```bash
git submodule add -b develop https://github.com/turnitin/moodle-plagiarism_turnitinsim.git plagiarism/turnitinsim
```

### LOCAL

- https://github.com/moodleuulm/moodle-local_sandbox
```bash
git submodule add -b MOODLE_500_STABLE https://github.com/moodleuulm/moodle-local_sandbox.git local/sandbox
```

## Removed from core
- https://github.com/moodlehq/moodle-mod_chat
```bash
git submodule add -b main https://github.com/moodlehq/moodle-mod_chat.git mod/chat
```
- https://github.com/moodlehq/moodle-mod_survey
```bash
git submodule add -b main https://github.com/moodlehq/moodle-mod_survey.git mod/survey
```

## Take a Look

- https://github.com/moodleworkplace/moodle-block_rbreport
```bash
git submodule add -b MOODLE_500_STABLE https://github.com/moodleworkplace/moodle-block_rbreport.git blocks/rbreport
```
## STACK question type - TODO!
- https://github.com/maths/moodle-qbehaviour_dfexplicitvaildate
```bash
git submodule add -b master https://github.com/maths/moodle-qbehaviour_dfexplicitvaildate.git question/behaviour/dfexplicitvaildate
```
- https://github.com/maths/moodle-qbehaviour_dfcbmexplicitvaildate
```bash
git submodule add -b master https://github.com/maths/moodle-qbehaviour_dfcbmexplicitvaildate.git question/behaviour/dfcbmexplicitvaildate
```
- https://github.com/maths/moodle-qbehaviour_adaptivemultipart
```bash
git submodule add -b master https://github.com/maths/moodle-qbehaviour_adaptivemultipart.git question/behaviour/adaptivemultipart
```		
- https://github.com/maths/moodle-qtype_stack
```bash
git submodule add -b master https://github.com/maths/moodle-qtype_stack.git question/type/stack
``` 
