<?xml version="1.0"?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
	<xsl:output omit-xml-declaration="yes" indent="yes"/>
	<xsl:strip-space elements="*"/>

	<!-- Define the Elements to Remove by Name -->
	<xsl:param name="removeElementsNamed" select="'|titlestmt|creation|repository|head|frontmatter|eadid|filedesc|profiledesc|'"/>

	<!-- This is the identity transformation; copies everything -->
	<xsl:template match="node()|@*" name="identity">
		<xsl:copy>
			<xsl:apply-templates select="node()|@*"/>
		</xsl:copy>
	</xsl:template>

	<!-- This removes the elements named above -->
	<xsl:template match="*">
		<xsl:if test="not(contains($removeElementsNamed,concat('|', name(), '|')))">
			<xsl:call-template name="identity"/>
		</xsl:if>
	</xsl:template>

	<!-- Deletes all the elements with the audience attribute set to "internal"  -->
	<xsl:template match="*[@audience='internal']"/>

	<!-- Fixes the extent statement-->
	<!-- Cubic Feet was an attribute; this appends it to the value of the element-->
	<!-- (It also updates to Linear Feet to be consistent across repositories) -->
	<xsl:template match="*[@type='Cubic Feet']">
		<xsl:copy>
			<xsl:value-of select="concat(., ' Linear Feet')"/>
		</xsl:copy>
	</xsl:template>


	<!-- Fixes the unitid statement-->
	<!-- removes the first three characters from the value; "88/" which isn't needed-->
	<xsl:template match="*[@label='Identification']">
		<xsl:copy>
			<xsl:value-of select="substring(.,4)"/>
		</xsl:copy>
	</xsl:template>

</xsl:stylesheet>
