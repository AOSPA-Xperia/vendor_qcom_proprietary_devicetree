
# add-overlay defines the target with following naming convention:
# <base>-<board>-dtbs = base.dtb board.dtbo
#
# Combined dtb target is also generated using the fdt_overlay tool.
# dtb-y += <base>-<board>.dtb

add-overlays = $(foreach o,$1,$(foreach b,$2,$(eval $(basename $b)-$(basename $o)-dtbs = $b $o) $(basename $b)-$(basename $o).dtb))

# kalama-dtb-y is list of DTBs to install when doing non-overlay build
# kalama-overlays-dtb-y is list of DTBs and DTBOs to install when doing overlay-supported build
# see DTB_TYPES from scripts/Makefile.dtbinst and install_dtbs from build.config.msm.common

ifneq ($(CONFIG_ARCH_QTI_VM), y)
SOMC_TARGET_PRODUCT := pdx234
SOMC_TARGET_OPERATOR := generic
SOMC_PLATFORM := yodo

SOMC_PRODUCT_OPERATOR = $(SOMC_TARGET_PRODUCT)_$(SOMC_TARGET_OPERATOR)

WAIPIO_BASE_DTB += waipio.dtb waipio-v2.dtb
WAIPIO_APQ_BASE_DTB += waipiop.dtb waipiop-v2.dtb

WAIPIO_BOARDS += \
		 waipio-rumi-overlay.dtbo \
		 waipio-mtp-pm8008-overlay.dtbo \
		 waipio-cdp-pm8008-overlay.dtbo \
		 waipio-qrd-pm8008-overlay.dtbo \
		 waipio-atp-pm8008-overlay.dtbo \
		 waipio-mtp-pm8010-overlay.dtbo \
		 waipio-cdp-pm8010-overlay.dtbo \
		 waipio-qrd-pm8010-overlay.dtbo \
		 waipio-qrd-pm8010-2s-overlay.dtbo \
		 waipio-atp-pm8010-overlay.dtbo

NOAPQ_WAIPIO_BOARDS += \
		       waipiop-hdk-pm8010-overlay.dtbo \
		       waipio-lemur-mtp-pm8008-overlay.dtbo \
		       waipio-lemur-mtp-pm8010-overlay.dtbo \
		       waipio-lemur-cdp-pm8008-overlay.dtbo \
		       waipio-lemur-cdp-pm8010-overlay.dtbo \
		       waipio-kiwi-mtp-pm8008-overlay.dtbo \
		       waipio-kiwi-mtp-pm8010-overlay.dtbo

waipio-dtb-$(CONFIG_ARCH_WAIPIO) += \
	$(call add-overlays, $(WAIPIO_BOARDS) $(NOAPQ_WAIPIO_BOARDS),$(WAIPIO_BASE_DTB))\
	$(call add-overlays, $(WAIPIO_BOARDS) $(APQ_WAIPIO_BOARDS),$(WAIPIO_APQ_BASE_DTB))
waipio-overlays-dtb-$(CONFIG_ARCH_WAIPIO) += $(WAIPIO_BOARDS) $(NOAPQ_WAIPIO_BOARDS) $(WAIPIO_BASE_DTB) $(WAIPIO_APQ_BASE_DTB)
dtb-y += $(waipio-dtb-y)


KALAMA_BASE_DTB += kalama.dtb kalama-v2.dtb kalama-sg.dtb kalama-qcm.dtb
KALAMA_APQ_BASE_DTB += kalamap.dtb kalamap-v2.dtb kalamap-sg.dtb kalamap-qcs.dtb

KALAMA_BOARDS += \
		 kalama-mtp-overlay.dtbo \
		 kalama-mtp-nfc-overlay.dtbo \
		 kalama-cdp-overlay.dtbo \
		 kalama-cdp-wsa883x-overlay.dtbo \
		 kalama-cdp-nfc-overlay.dtbo \
		 kalama-atp-overlay.dtbo \
		 kalama-rcm-overlay.dtbo \
		 kalama-qrd-overlay.dtbo \
		 kalama-sg-hhg-overlay.dtbo \
		 kalamap-hdk-overlay.dtbo \
		 kalamap-sg-hhg-overlay.dtbo \
		 kalamap-rb5-gen2-overlay.dtbo \
		 kalamap-aim300-overlay.dtbo

NOAPQ_KALAMA_BOARDS += \
		 kalama-rumi-overlay.dtbo \
		 kalama-pinn-cdp-overlay.dtbo \
		 kalama-pinn-mtp-overlay.dtbo \
		 kalama-baagha-cdp-overlay.dtbo \
		 kalama-baagha-mtp-overlay.dtbo

ifeq ($(SOMC_PRODUCT_OPERATOR),pdx234_generic)
KALAMA_SOMC_BOARDS += \
		kalama-yodo-pdx234_generic-overlay.dtbo
endif
ifeq ($(SOMC_PLATFORM),yodo)
kalama-dtb-$(CONFIG_ARCH_KALAMA) += \
	$(call add-overlays, $(KALAMA_SOMC_BOARDS),$(KALAMA_BASE_DTB))
kalama-overlays-dtb-$(CONFIG_ARCH_KALAMA) += $(KALAMA_SOMC_BOARDS) $(KALAMA_BASE_DTB)
else
kalama-dtb-$(CONFIG_ARCH_KALAMA) += \
	$(call add-overlays, $(KALAMA_BOARDS) $(NOAPQ_KALAMA_BOARDS),$(KALAMA_BASE_DTB))\
	$(call add-overlays, $(KALAMA_BOARDS) $(APQ_KALAMA_BOARDS),$(KALAMA_APQ_BASE_DTB))
kalama-overlays-dtb-$(CONFIG_ARCH_KALAMA) += $(KALAMA_BOARDS) $(NOAPQ_KALAMA_BOARDS) $(KALAMA_BASE_DTB) $(KALAMA_APQ_BASE_DTB)
kalama_le-overlays-dtb-$(CONFIG_ARCH_KALAMA) += $(KALAMA_BOARDS) $(NOAPQ_KALAMA_BOARDS) $(KALAMA_BASE_DTB) $(KALAMA_APQ_BASE_DTB)
kalama_lu-overlays-dtb-$(CONFIG_ARCH_KALAMA) += $(KALAMA_BOARDS) $(NOAPQ_KALAMA_BOARDS) $(KALAMA_BASE_DTB) $(KALAMA_APQ_BASE_DTB)
endif
dtb-y += $(kalama-dtb-y)

CROW_BASE_DTB += crow.dtb

CROW_BOARDS += \
		crow-rumi-overlay.dtbo \
		crow-atp-overlay.dtbo \
		crow-idp-overlay.dtbo \
		crow-idp-wcd9395-wcd-dmic-overlay.dtbo \
		crow-idp-wcd9395-dmic-overlay.dtbo \
		crow-idp-wcd9395-aatc-overlay.dtbo \
		crow-idp-rcm-overlay.dtbo \
		crow-qrd-overlay.dtbo

kalama-dtb-$(CONFIG_ARCH_CROW) += \
	$(call add-overlays, $(CROW_BOARDS) ,$(CROW_BASE_DTB))
kalama-overlays-dtb-$(CONFIG_ARCH_CROW) += $(CROW_BOARDS) $(CROW_BASE_DTB)
dtb-y += $(kalama-dtb-y)

KHAJE_BASE_DTB += khaje.dtb khajep.dtb khajeq.dtb khajeg.dtb khaje-3gb.dtb

KHAJE_BOARDS += \
                 khaje-idp-overlay.dtbo \
                 khaje-qrd-overlay.dtbo \
		 khaje-qrd-hvdcp3p5-overlay.dtbo \
		 khaje-qrd-nowcd9375-overlay.dtbo \
                 khaje-idp-nopmi-overlay.dtbo \
                 khaje-qrd-nopmi-overlay.dtbo \
                 khaje-idps-display-90hz-overlay.dtbo \
                 khaje-atp-overlay.dtbo \
                 khaje-idp-usbc-overlay.dtbo \
                 khaje-idp-pm8010-overlay.dtbo \
                 khajep-atp-overlay.dtbo \
                 khajep-qrd-overlay.dtb \
                 khajep-qrd-hvdcp3p5-overlay.dtbo \
                 khajep-qrd-nowcd9375-overlay.dtbo \
                 khajep-qrd-nopmi-overlay.dtbo \
                 khajep-idp-overlay.dtbo \
                 khajep-idp-nopmi-overlay.dtbo \
                 khajep-idp-usbc-overlay.dtbo \
                 khajep-idp-pm8010-overlay.dtbo \
                 khajep-idps-display-90hz-overlay.dtbo \
                 khajeq-atp-overlay.dtbo \
                 khajeq-qrd-overlay.dtbo \
                 khajeq-qrd-hvdcp3p5-overlay.dtbo \
                 khajeq-qrd-nowcd9375-overlay.dtbo \
                 khajeq-qrd-nopmi-overlay.dtbo \
                 khajeq-idp-overlay.dtbo \
                 khajeq-idp-nopmi-overlay.dtbo \
                 khajeq-idp-usbc-overlay.dtbo \
                 khajeq-idp-pm8010-overlay.dtbo \
                 khajeq-idps-display-90hz-overlay.dtbo \
                 khajeg-atp-overlay.dtbo \
		 khajeg-qrd-overlay.dtbo \
		 khajeg-qrd-hvdcp3p5-overlay.dtbo \
		 khajeg-qrd-nowcd9375-overlay.dtbo \
		 khajeg-qrd-nopmi-overlay.dtbo \
		 khajeg-idp-overlay.dtbo \
		 khajeg-idp-nopmi-overlay.dtbo \
		 khajeg-idp-usbc-overlay.dtbo \
		 khajeg-idp-pm8010-overlay.dtbo \
		 khajeg-idps-display-90hz-overlay.dtbo

bengal-dtb-$(CONFIG_ARCH_KHAJE) += \
        $(call add-overlays, $(KHAJE_BOARDS) ,$(KHAJE_BASE_DTB))
bengal-overlays-dtb-$(CONFIG_ARCH_KHAJE) += $(KHAJE_BOARDS) $(KHAJE_BASE_DTB)
dtb-y += $(bengal-dtb-y)

KONA_BASE_DTB += kona-iot.dtb kona-iot-v2.dtb kona-iot-v2.1.dtb kona-7230-iot-v2.1.dtb
KONA_LE_BASE_DTB += kona-7230-iot-v2.1.dtb qrb5165-iot.dtb qrb5165n-iot.dtb qrb3165-iot.dtb qrb3165n-iot.dtb

KONA_BOARDS += \
                 kona-hdk-overlay.dtbo \
                 kona-rb5-HDMI-overlay.dtbo \
                 kona-rb5-HDMI-overlay-new.dtbo \
                 kona-rb5-overlay-new.dtbo \
                 kona-iot-v2.1-vc-overlay.dtbo \
		 kona-7230-iot-rb5-overlay.dtbo \
		 kona-rb5-overlay.dtbo \
		 kona-qrd-wingmate-overlay.dtbo \
		 kona-mtp-wingmate-overlay.dtbo


KONA_LE_BOARDS += \
		 qrb5165-iot-rb5-overlay.dtbo \
		 qrb3165-iot-rb5-overlay.dtbo \
		 kona-7230-iot-rb5-overlay.dtbo \
		 qrb5165n-iot-v2-rb5-overlay.dtbo \
		 qrb3165n-iot-v2-rb5-overlay.dtbo

kona-dtb-$(CONFIG_ARCH_KONA) += \
        $(call add-overlays, $(KONA_BOARDS) ,$(KONA_BASE_DTB)) \
	$(call add-overlays, $(KONA_LE_BOARDS) ,$(KONA_LE_BASE_DTB))
kona-overlays-dtb-$(CONFIG_ARCH_KONA) += $(KONA_BOARDS) $(KONA_BASE_DTB)
kona_le-overlays-dtb-$(CONFIG_ARCH_KONA) += $(KONA_LE_BOARDS) $(KONA_LE_BASE_DTB)
dtb-y += $(kona-dtb-y)

MONACO_BASE_DTB += monaco.dtb monacop.dtb

MONACO_BOARDS += \
        monaco-idp-v1-overlay.dtbo \
        monaco-standalone-idp-v1-overlay.dtbo \
        monaco-idp-v2-overlay.dtbo \
        monaco-standalone-idp-v2-overlay.dtbo \
        monaco-idp-v3-overlay.dtbo \
        monaco-standalone-idp-v3-overlay.dtbo \
	monaco-wdp-v1-overlay.dtbo \
	monaco-standalone-wdp-v1-overlay.dtbo \
	monaco-atp-v1-overlay.dtbo \
	monaco-standalone-atp-v1-overlay.dtbo

monaco-dtb-$(CONFIG_ARCH_MONACO) += \
        $(call add-overlays, $(MONACO_BOARDS) ,$(MONACO_BASE_DTB))
monaco-overlays-dtb-$(CONFIG_ARCH_MONACO) += $(MONACO_BOARDS) $(MONACO_BASE_DTB)
dtb-y += $(monaco-dtb-y)

cinder-dtb-$(CONFIG_ARCH_CINDER) += cinder-ru-rumi.dtb \
	cinder-du-rumi.dtb \
	cinder-ru-idp.dtb \
	cinder-ru-idp-2gb.dtb \
	cinder-du-idp.dtb \
	cinder-du-x100.dtb \
	cinder-du-idp-4gb.dtb \
	cinder-v2-ru-idp.dtb \
	cinder-v2-ru-idp-2gb.dtb \
	cinder-v2-du-idp.dtb \
	cinder-v2-du-idp-4gb.dtb \
	cinder-v2-du-x100.dtb \
	cinder-v2-ru-rumi.dtb \
	cinder-v2-du-rumi.dtb
dtb-y += $(cinder-dtb-y)

QCS405_BASE_DTB += qcs405.dtb qcs407.dtb

QCS405_BOARDS += qcs405-iot-sku1-overlay.dtbo \
	qcs405-iot-sku2-overlay.dtbo \
	qcs405-iot-sku3-overlay.dtbo \
	qcs405-iot-sku4-overlay.dtbo \
	qcs405-iot-sku5-overlay.dtbo \
	qcs405-iot-sku6-overlay.dtbo \
	qcs405-iot-sku7-overlay.dtbo \
	qcs405-iot-sku8-overlay.dtbo \
	qcs405-iot-sku9-overlay.dtbo \
	qcs405-iot-sku10-overlay.dtbo \
	qcs405-iot-sku12-overlay.dtbo \
	qcs405-iot-sku13-overlay.dtbo

qcs405-dtb-$(CONFIG_ARCH_QCS405) += \
        $(call add-overlays, $(QCS405_BOARDS) ,$(QCS405_BASE_DTB))

qcs405-overlays-dtb-$(CONFIG_ARCH_QCS405) += $(QCS405_BOARDS) $(QCS405_BASE_DTB)
dtb-y += $(qcs405-dtb-y)

TRINKET_BASE_DTB += trinket-iot.dtb trinketp-iot.dtb

TRINKET_BOARDS += \
	trinket-iot-idp-overlay.dtbo \
	trinketp-iot-idp-overlay.dtbo \
	trinket-iot-dp-idp-overlay.dtbo \
	trinket-iot-external-codec-idp-overlay.dtbo \
	trinket-iot-usbc-external-codec-idp-overlay.dtbo \
	trinket-iot-usbc-idp-overlay.dtbo \
	trinketp-iot-dp-idp-overlay.dtbo \
	trinketp-iot-external-codec-idp-overlay.dtbo \
	trinketp-iot-usbc-external-codec-idp-overlay.dtbo \
	trinketp-iot-usbc-idp-overlay.dtbo

trinket-dtb-$(CONFIG_ARCH_TRINKET) += \
        $(call add-overlays, $(TRINKET_BOARDS) ,$(TRINKET_BASE_DTB))
trinket-overlays-dtb-$(CONFIG_ARCH_TRINKET) += $(TRINKET_BOARDS) $(TRINKET_BASE_DTB)
dtb-y += $(trinket-dtb-y)

kaka-dtb-$(CONFIG_ARCH_KAKA) += kaka-rumi.dtb
dtb-y += $(kaka-dtb-y)

SA8155_BASE_DTB += sa8155.dtb sa8155-v2.dtb
SA8155P_BASE_DTB += sa8155p.dtb sa8155p-v2.dtb
SA8195P_BASE_DTB += sa8195p.dtb

SA8155_BOARDS += \
		 sa8155-adp-star-overlay.dtbo \
		 sa8155-adp-air-overlay.dtbo

SA8155P_BOARDS += \
		       sa8155p-adp-star-overlay.dtbo \
		       sa8155p-adp-air-overlay.dtbo

SA8195P_BOARDS += sa8195p-adp-star-overlay.dtbo \
		  sa8195p-adp-air-overlay.dtbo

gen3auto-dtb-$(CONFIG_ARCH_SA8155) += \
	$(call add-overlays, $(SA8155_BOARDS),$(SA8155_BASE_DTB))\
	$(call add-overlays, $(SA8155P_BOARDS),$(SA8155P_BASE_DTB))
gen3auto-overlays-dtb-$(CONFIG_ARCH_SA8155) += $(SA8155_BOARDS) $(SA8155P_BOARDS) $(SA8155_BASE_DTB) $(SA8155P_BASE_DTB)

gen3auto-dtb-$(CONFIG_ARCH_SA8195) += \
		$(call add-overlays, $(SA8195P_BOARDS),$(SA8195P_BASE_DTB))
gen3auto-overlays-dtb-$(CONFIG_ARCH_SA8195) += $(SA8195P_BOARDS) $(SA8195P_BASE_DTB)

dtb-y += $(gen3auto-dtb-y)

SA6155_BASE_DTB += sa6155.dtb
SA6155P_BASE_DTB += sa6155p.dtb

SA6155_BOARDS += sa6155-adp-star-overlay.dtbo \
		sa6155-adp-air-overlay.dtbo

SA6155P_BOARDS += sa6155p-adp-star-overlay.dtbo \
		sa6155p-adp-air-overlay.dtbo

sdmsteppeauto-dtb-$(CONFIG_ARCH_SA6155) += \
	$(call add-overlays, $(SA6155_BOARDS),$(SA6155_BASE_DTB))\
	$(call add-overlays, $(SA6155P_BOARDS),$(SA6155P_BASE_DTB))
sdmsteppeauto-overlays-dtb-$(CONFIG_ARCH_SA6155) += $(SA6155_BOARDS) $(SA6155P_BOARDS) $(SA6155_BASE_DTB) $(SA6155P_BASE_DTB)

dtb-y += $(sdmsteppeauto-dtb-y)

SDM670_BASE_DTB += qcs605.dtb

SDM670_BOARDS += \
		 qcs605-mtp-overlay.dtbo \
		 qcs605-cdp-overlay.dtbo \
		 qcs605-360camera-overlay.dtbo \
		 qcs605-external-codec-mtp-overlay.dtbo

qcs605-dtb-$(CONFIG_ARCH_SDM670) += \
	$(call add-overlays, $(SDM670_BOARDS) ,$(SDM670_BASE_DTB))
qcs605-overlays-dtb-$(CONFIG_ARCH_SDM670) += $(SDM670_BOARDS) $(SDM670_BASE_DTB)
dtb-y += $(qcs605-dtb-y)

LEMANS_BASE_DTB		+= lemans.dtb
LEMANS_IVI_BASE_DTB	+= lemans-ivi.dtb
LEMANS_ADAS_HIGH_BASE_DTB += lemans-adas-high.dtb
LEMANS_IVI_ADAS_BASE_DTB  += lemans-ivi-adas.dtb

LEMANS_BOARDS		+= lemans-rumi-overlay.dtbo
LEMANS_IVI_BOARDS	+= lemans-ivi-adp-air-overlay.dtbo \
			   lemans-ivi-adp-star-overlay.dtbo \
			   lemans-ivi-qam-star-overlay.dtbo
LEMANS_ADAS_HIGH_BOARDS += lemans-adas-high-adp-air-overlay.dtbo \
			   lemans-adas-high-adp-star-overlay.dtbo \
			   lemans-adas-high-qam-star-overlay.dtbo

LEMANS_IVI_ADAS_BOARDS  += lemans-ivi-adas-qam-star-overlay.dtbo \
			   lemans-ivi-adas-adp-star-overlay.dtbo

gen4auto-dtb-$(CONFIG_ARCH_LEMANS) += \
	$(call add-overlays, $(LEMANS_IVI_BOARDS),$(LEMANS_IVI_BASE_DTB))\
	$(call add-overlays, $(LEMANS_ADAS_HIGH_BOARDS),$(LEMANS_ADAS_HIGH_BASE_DTB))\
	$(call add-overlays, $(LEMANS_IVI_ADAS_BOARDS),$(LEMANS_IVI_ADAS_BASE_DTB))

gen4auto-overlays-dtb-$(CONFIG_ARCH_LEMANS) +=  \
	$(LEMANS_IVI_BOARDS) $(LEMANS_ADAS_HIGH_BOARDS) $(LEMANS_IVI_BASE_DTB) $(LEMANS_ADAS_HIGH_BASE_DTB) \
	$(LEMANS_IVI_ADAS_BOARDS) $(LEMANS_IVI_ADAS_BASE_DTB)

MONACO_AUTO_BASE_DTB	+= monaco_auto-rumi.dtb
MONACO_AUTO_BOARDS	+= monaco_auto-rumi-overlay.dtbo

gen4auto-dtb-$(CONFIG_ARCH_MONACO_AUTO) += \
	$(call add-overlays, $(MONACO_AUTO_BOARDS),$(MONACO_AUTO_BASE_DTB))

gen4auto-overlays-dtb-$(CONFIG_ARCH_MONACO_AUTO) +=  \
	$(MONACO_AUTO_BOARDS) $(MONACO_AUTO_BASE_DTB)

dtb-y += $(gen4auto-dtb-y)

sdxpinn-dtb-$(CONFIG_ARCH_SDXPINN) += sdxpinn-rumi.dtb sa525m-rumi.dtb \
		sdxpinn-idp-mbb.dtb
dtb-y += $(sdxpinn-dtb-y)

SA410M_AUTO_BASE_DTB += sa410m.dtb
SA410M_AUTO_BOARDS += \
		sa410m-rumi-overlay.dtbo \
		sa410m-nand-idp-overlay.dtbo \
		sa410m-emmc-idp-overlay.dtbo \
		sa410m-nand-ccard-overlay.dtbo \
		sa410m-emmc-ccard-overlay.dtbo

sa410m_auto-dtb-$(CONFIG_ARCH_SA410M) += \
	$(call add-overlays, $(SA410M_AUTO_BOARDS) ,$(SA410M_AUTO_BASE_DTB))
sa410m_auto-overlays-dtb-$(CONFIG_ARCH_SA410M) += $(SA410M_AUTO_BOARDS) $(SA410M_AUTO_BASE_DTB)
dtb-y += $(sa410m_auto-dtb-y)

SA8155_LA_GVM_BASE_DTB += sa8155-vm-la.dtb

SA8155_LA_GVM_BOARDS += \
		   sa8155-vm-la-overlay.dtbo

LEMANS_LV_GVM_BASE_DTB += lemans-vm-lv.dtb

LEMANS_LV_GVM_BOARDS += \
		lemans-vm-lv-overlay.dtbo

LEMANS_LA_GVM_BASE_DTB += lemans-vm-la.dtb

LEMANS_LA_GVM_BOARDS += \
		lemans-vm-la-overlay.dtbo

DIREWOLF_LV_GVM_BASE_DTB += direwolf-vm-lv.dtb

DIREWOLF_LV_GVM_BOARDS += \
                   direwolf-vm-lv-overlay.dtbo

DIREWOLF_LA_GVM_BASE_DTB += direwolf-vm-la.dtb

DIREWOLF_LA_GVM_BOARDS += \
                   direwolf-vm-la-overlay.dtbo

DIREWOLF_MULTI_GVM_BASE_DTB += \
		direwolf-vm-la-mt.dtb \
		direwolf-vm-lv-mt.dtb

DIREWOLF_MULTI_GVM_BOARDS += \
		direwolf-vm-la-mt-overlay.dtbo \
		direwolf-vm-lv-mt-overlay.dtbo

LEMANS_MULTI_GVM_BASE_DTB += \
		lemans-vm-la-mt.dtb \
		lemans-vm-lv-mt.dtb

LEMANS_MULTI_GVM_BOARDS += \
		lemans-vm-la-mt-overlay.dtbo \
		lemans-vm-lv-mt-overlay.dtbo

SA8195_LA_GVM_BASE_DTB += sa8195-vm-la.dtb

SA8195_LA_GVM_BOARDS += \
                   sa8195-vm-la-overlay.dtbo

DIREWOLF_LV_GVM_HEADLESS_BASE_DTB += direwolf-vm-lv-headless-mt.dtb

DIREWOLF_LV_GVM_HEADLESS_BOARDS += \
                   direwolf-vm-lv-headless-mt-overlay.dtbo

autogvm-dtb-$(CONFIG_QTI_QUIN_GVM) += \
	$(call add-overlays, $(SA8155_LA_GVM_BOARDS),$(SA8155_LA_GVM_BASE_DTB)) \
	$(call add-overlays, $(DIREWOLF_LV_GVM_BOARDS),$(DIREWOLF_LV_GVM_BASE_DTB)) \
	$(call add-overlays, $(SA8195_LA_GVM_BOARDS),$(SA8195_LA_GVM_BASE_DTB)) \
	$(call add-overlays, $(DIREWOLF_LA_GVM_BOARDS),$(DIREWOLF_LA_GVM_BASE_DTB)) \
	$(call add-overlays, $(LEMANS_LV_GVM_BOARDS),$(LEMANS_LV_GVM_BASE_DTB)) \
	$(call add-overlays, $(LEMANS_LA_GVM_BOARDS),$(LEMANS_LA_GVM_BASE_DTB)) \
	$(call add-overlays, $(DIREWOLF_LV_GVM_HEADLESS_BOARDS),$(DIREWOLF_LV_GVM_HEADLESS_BASE_DTB)) \
	$(call add-overlays, $(DIREWOLF_MULTI_GVM_BOARDS),$(DIREWOLF_MULTI_GVM_BASE_DTB)) \
	$(call add-overlays, $(LEMANS_MULTI_GVM_BOARDS),$(LEMANS_MULTI_GVM_BASE_DTB))

autogvm-overlays-dtb-$(CONFIG_QTI_QUIN_GVM) += \
	$(SA8155_LA_GVM_BOARDS) $(DIREWOLF_LV_GVM_BOARDS) $(SA8155_LA_GVM_BASE_DTB) $(DIREWOLF_LV_GVM_BASE_DTB) \
	$(SA8195_LA_GVM_BOARDS) $(SA8195_LA_GVM_BASE_DTB) $(DIREWOLF_LA_GVM_BOARDS) $(DIREWOLF_LA_GVM_BASE_DTB) \
	$(LEMANS_LA_GVM_BOARDS) $(LEMANS_LA_GVM_BASE_DTB) $(LEMANS_LV_GVM_BOARDS) $(LEMANS_LV_GVM_BASE_DTB) \
	$(DIREWOLF_LV_GVM_HEADLESS_BOARDS) $(DIREWOLF_LV_GVM_HEADLESS_BASE_DTB) $(DIREWOLF_MULTI_GVM_BOARDS) \
	$(DIREWOLF_MULTI_GVM_BASE_DTB) $(LEMANS_MULTI_GVM_BOARDS) $(LEMANS_MULTI_GVM_BASE_DTB)

dtb-y += $(autogvm-dtb-y)

SCUBA_AUTO_BASE_DTB += scuba_auto.dtb
SCUBA_AUTO_BOARDS += \
		scuba_auto-idp-overlay.dtbo \
		scuba_auto-qrd-overlay.dtbo
scuba_auto-dtb-$(CONFIG_ARCH_SCUBA_AUTO) += \
	$(call add-overlays, $(SCUBA_AUTO_BOARDS) ,$(SCUBA_AUTO_BASE_DTB))
scuba_auto-overlays-dtb-$(CONFIG_ARCH_SCUBA_AUTO) += $(SCUBA_AUTO_BOARDS) $(SCUBA_AUTO_BASE_DTB)
dtb-y += $(scuba_auto-dtb-y)

endif

ifeq ($(CONFIG_ARCH_LEMANS), y)
ifeq ($(CONFIG_ARCH_QTI_VM), y)

LEMANS_GH_LA_GVM_QAM_BASE_DTB += lemans-gunyah-vm-qam.dtb
LEMANS_GH_LA_GVM_QAM_BOARDS += lemans-gunyah-vm-qam-overlay.dtbo

LEMANS_GH_LA_GVM_VP_BASE_DTB += lemans-gunyah-vm-vp.dtb
LEMANS_GH_LA_GVM_VP_BOARDS += lemans-gunyah-vm-vp-overlay.dtbo

LEMANS_GH_LA_GVM_COB_BASE_DTB += lemans-gunyah-vm-cob.dtb
LEMANS_GH_LA_GVM_COB_BOARDS += lemans-gunyah-vm-cob-overlay.dtbo

autoghgvm-dtb-$(CONFIG_ARCH_QTI_VM) += \
	$(call add-overlays, $(LEMANS_GH_LA_GVM_QAM_BOARDS),$(LEMANS_GH_LA_GVM_QAM_BASE_DTB)) \
	$(call add-overlays, $(LEMANS_GH_LA_GVM_VP_BOARDS),$(LEMANS_GH_LA_GVM_VP_BASE_DTB)) \
	$(call add-overlays, $(LEMANS_GH_LA_GVM_COB_BOARDS),$(LEMANS_GH_LA_GVM_COB_BASE_DTB))

autoghgvm-overlays-dtb-$(CONFIG_ARCH_QTI_VM) += \
	$(LEMANS_GH_LA_GVM_QAM_BOARDS) $(LEMANS_GH_LA_GVM_QAM_BASE_DTB) \
	$(LEMANS_GH_LA_GVM_VP_BOARDS) $(LEMANS_GH_LA_GVM_VP_BASE_DTB) \
	$(LEMANS_GH_LA_GVM_COB_BOARDS) $(LEMANS_GH_LA_GVM_COB_BASE_DTB)

dtb-y += $(autoghgvm-dtb-y)
endif
endif

ifeq ($(CONFIG_ARCH_KALAMA), y)
ifeq ($(CONFIG_ARCH_QTI_VM), y)
kalama_tuivm-dtb-$(CONFIG_ARCH_QTI_VM) += kalama-vm-rumi.dtb \
                 kalama-vm-mtp.dtb \
                 kalama-vm-cdp.dtb \
                 kalama-vm-qrd.dtb \
                 kalama-vm-hdk.dtb \
                 kalama-vm-hhg.dtb \
                 kalama-oemvm-cdp.dtb \
                 kalama-oemvm-mtp.dtb \
                 kalama-oemvm-qrd.dtb \
                 kalama-oemvm-rumi.dtb \
                 kalamap-oemvm-hdk.dtb \
                 kalamap-oemvm-hhg.dtb
dtb-y += $(kalama_tuivm-dtb-y)
endif
endif

ifeq ($(CONFIG_ARCH_CROW), y)
ifeq ($(CONFIG_ARCH_QTI_VM), y)
kalama_tuivm-dtb-$(CONFIG_ARCH_QTI_VM) += crow-vm-rumi.dtb \
	crow-vm-atp.dtb \
	crow-vm-idp-wcd9395-aatc.dtb \
	crow-vm-idp-wcd9395-dmic.dtb \
	crow-vm-idp-wcd9395-wcd-dmic.dtb \
	crow-vm-idp.dtb \
	crow-vm-idp-rcm.dtb \
	crow-vm-qrd.dtb \
	crow-oemvm-atp.dtb \
	crow-oemvm-idp-wcd9395-aatc.dtb \
	crow-oemvm-idp-wcd9395-dmic.dtb \
	crow-oemvm-idp-wcd9395-wcd-dmic.dtb \
	crow-oemvm-idp.dtb \
	crow-oemvm-idp-rcm.dtb \
	crow-oemvm-qrd.dtb
dtb-y += $(kalama_tuivm-dtb-y)
endif
endif

ifeq ($(CONFIG_ARCH_WAIPIO), y)
ifeq ($(CONFIG_ARCH_QTI_VM), y)
waipio_tuivm-dtb-$(CONFIG_ARCH_QTI_VM) += waipio-vm-mtp.dtb \
        waipio-vm-cdp.dtb \
        waipio-vm-qrd.dtb \
        waipio-vm-rumi.dtb \
	waipio-oemvm-cdp.dtb \
	waipio-oemvm-mtp.dtb \
	waipio-oemvm-qrd.dtb \
	waipio-oemvm-rumi.dtb
dtb-y += $(waipio_tuivm-dtb-y)
endif
endif

sdxbaagha-dtb-$(CONFIG_ARCH_SDXBAAGHA) += sdxbaagha-rumi.dtb \
	sdxbaagha-mtp.dtb \
	sdxbaagha-cdp.dtb
dtb-y += $(sdxbaagha-dtb-y)

always-y        := $(dtb-y)
subdir-y        := $(dts-dirs)
clean-files     := *.dtb *.dtbo
